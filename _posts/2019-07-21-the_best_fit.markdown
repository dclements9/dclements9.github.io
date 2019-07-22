---
layout: post
title:      "The Best Fit"
date:       2019-07-21 22:51:41 -0400
permalink:  the_best_fit
---

Ruby, and Rails especially, make heavy use of conventions. This allows for developers and teams to easily understand how to follow and add to code. It also minimizes the risk of unnecessary bugs while writing. However, how to properly implement admin functionality is still a bit controversial.

Depending on the size of the application and admin functionality, the ‘best’ method can vary. While some developers prefer a gem called ‘active-admin’, others prefer namespacing, and others prefer simply adding admin functionality for logged in users. 
	
I’m fascinated by the implementation of authentication and authorization. Which is why I decided to learn first hand what it was like to build such a feature. While the gem ‘active-admin’ seemed like a solid choice, the functionality seemed like much more than what I needed. I couldn’t justify the dependence on another gem for so much of what I didn’t need. My next choice was namespacing, which felt like the way to go from the start.

Rails apps are built with the MVC architecture in mind. The Model is responsible for logic concerns, the Controller (I know, the C comes after the V) is responsible for passing data from the Model to the View, which is responsible for displaying a page (view) to the user. In this case, my EquipmentController needed admin functionality to edit, delete, and add new (you guessed it) equipment. I wanted the non-admin user to only be able to view all equipment (index) or a single piece of equipment (show).

With usual DRY (Don’t repeat yourself) fashion, it’s best to keep routes from getting unwieldy. Which is when Rails comes in to save the day! Enter namespacing. The routes for this app would look like this: 
	
```namespace :admin do
resources :equipment, only: [:edit, :update, :new, :create]
end```
	
Keeping admin access separate from the non-admin controller.

The paired controller would be nested in an admin folder and look like:

```class Admin::EquipmentController < ApplicationController
def new
	
	end```
	
	The views would also be nested inside an /admin/equipment folder to keep a separation of concerns from admin and non-admin functionality. With the namespacing all set, other routing paths are provided:
	```admin_equipment_new_path
	admin_equipment_path
	#...```
	
	Allowing again for the admin to stay separate from the non-admin equipment paths.

	While implementing the namespacing way was a clean way to separate the admin functionality. It felt like the opposite of keeping my code simple and readable. While it made it very clear what was going on, it was over complicated for such a simple task. Again, the admin simply need to be able to make small changes, add, or delete an object.

	Ultimately, I landed on the simple method, adding functionality to users with the admin attribute. The admin attribute would not be permitted on user creation, preventing random admins from being created:
	
```params.require(:user).permit(:email, :name, :password, :password_confirmation)```
	
Links would only be visible if a user was an admin:

```<%= link_to 'Add Equipment', new_equipment_path unless !current_user.admin? %>```
	
	
And before every admin action, it would check again for the user being an admin to avoid the pesky manual url inputs:
	
	```before_action :is_admin?, only: [:edit, :update, :new, :create, :destroy]```
	
Which ran this:
	
	```def is_admin?
	redirect_to equipment_index_path unless current_user.admin?
	end```
	
In the end, the simple implementation felt like the clean, developer friendly way to execute admin functionality. Which is really the goal in the end after solving a client’s or other real world problems.

I’m excited to use other methods in the future for different circumstances and see which one is the most manageable and preferred while working along side other developers.
