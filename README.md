# Generate email-safe html from haml

It makes writing html emails so much fun!

# Installation

 * clone this repo

 * cd into the newly cloned repo and run ```bundle exec guard```

# Usage

 * create a new folder for the email

 * create a file with a name like ```awesome_name_here.html.haml```, pick an awesome name though

 * write your email in haml & sass

 * when you save your ```.haml``` file, a ```.premailer.html``` file will be generated in the same folder, open this in your browser to preview

 * use the livereload browser plugin if you're into that

 * when you're done, view source or open the ```.premailer.html``` file and use that markup as your email

 * at this point, you should probably send a test to litmus.com, then send the email via mailchimp.com or some other awesome email sending service

 * if you're sending from gmail, hit ```CMD+a``` or ```CTRL+a``` in the web view (not view source) to copy the email and paste it into your gmail compose view

# Creds

This wouldn't be possible w/o premailer, haml, sass and guard
