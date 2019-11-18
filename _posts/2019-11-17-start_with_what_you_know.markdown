---
layout: post
title:      "Start With What You Know"
date:       2019-11-18 04:41:17 +0000
permalink:  start_with_what_you_know
---


Hara is a React/Redux app with a Rails/Ruby backend. After weeks of diving into React, Redux, and the synergy between them, I could go on and on about how amazing their features are. However while setting up the table associations on the Rails side of things, I noticed there wasn’t an easy to find guide on seeding for and creating many-to-many associations.

So without further ado, this is my quick guide per example on setting it up. I wanted to join the users & challenges tables so many users could complete many challenges. This results in challenges having many users and users having many challenges. With ActiveRecord, the clearest association seemed to be {:has_and_belongs_to_many }. For Further Reading: [https://api.rubyonrails.org/classes/ActiveRecord/Associations/ClassMethods.html], I find the Ruby on Rails docs to be the best source for documentation. With that being said, both users and challenges would need the association {:has_and_belongs_to_many } in their respective models.

From there, generating the join table is rather straightforward, especially with rails generators. Using 
rails g migration CreateUsersChallengesJoinTable

the migration would look like: 
class CreateUsersChallengesJoinTable <ActiveRecord::Migration[5.2]
  def change
    create_join_table :users, :challenges do |t|
      t.index [:user_id, :challenge_id]
      t.index [:challenge_id, :user_id]
    end
  end
end

Which only left me with the problem of how to properly seed the association.

While researching, I found many examples using .create to create the associated object as the first object was created. For example:
BeginnerLesson = Lesson.create(title: 'Beginner Class', description: "The Beginner Class for all.", date: "2019-12-01", start_time: "2000-01-01 08:00:00", end_time: "2000-01-01 09:00:00")
BeginnerLesson.users.create = (first_name: 'Joe', last_name: 'Shmo', email: 'jshmo@shmo.com', 
    password_digest: 'password', age: 22, rank: 3)

But I wanted to be able to create one object, then the second, in case the association was no longer needed or the object was needed for something other than the association. 

After a bit more research, looking into my older rails projects, and testing a bit (my favorite part - breaking things to learn new things and make them work). I realized the solution was quite simple, I simply needed to step back and think about what exactly I was creating. The users property of Challenge is simple an array of user objects! So the answer was simply:

BeginnerLesson = Lesson.create(title: 'Beginner Class', description: "The Beginner Class for all.", date: "2019-12-01", start_time: "2000-01-01 08:00:00", end_time: "2000-01-01 09:00:00")
BeginnerLesson.users = [JohnSmith, JaneDoe]
Having to go through this process also reminded me of the most important lesson I learned during Flatiron School. One I try to remember every time I get flustered, lost, or completely overwhelmed by what’s in front of me, “Start with what you know”. When you start breaking down each little piece, it all comes together like a beautiful puzzle. If you can’t figure out how to create a user, start with what you know, can you create an object? Do you know what properties a user will need? The bigger problems are really just smaller pieces placed together. Every problem can be broken apart, just  “Start with what you know”.
