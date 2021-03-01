# Rails Auto Reload

This is a short Video on **adding auto reload for rails applications**
-------------------------
Link to the : [YOUTUBE CHANNEL](https://www.youtube.com/channel/UC9j6pieJxlXmpq0k7kV1VDg)

Link to the video : not yet published

-------------------------------------------

* In the video i explain how to add Auto Reload for Rails     Applications.
It can be done with some few steps.

* Below you can read all the steps in text form.
For the video you can visit this LINK

* Check this **list** to see the different locations that we needed to add new codes


---------------------------------------

  For this we need to add **guard-livereload** and **rack-livereload** gem to our Gemfile.
  We need to add the gem to **Development Group** , because we need it only in Development
  ```
  group :development do
    gem 'guard-livereload', '~> 2.5', require: false
    gem 'rack-livereload'
  end
  ```
  Then in the terminal write :
  ```
  $ bundle install
  ```
  This command will download and configure all needed **Configs**
* Now in the Terminal write :
  ```
  $ bundle exec guard init livereload
  ```
  This command will add Guardfile to the project.
  This command will download and configure all needed **Configs**.
* Now we need to add the **middleware** to our **Rails middleware** stack
  For this open **config/environments/development.rb**
  Add the code below to the end of the file
  ```
  # Add Rack::LiveReload to the bottom of the middleware stack with the default options:
  config.middleware.insert_after ActionDispatch::Static, Rack::LiveReload
  ```

We are all set now all we need is running the rails Server again with :

```
$ rails s
```

and in a new tab of the **terminal** run :

```
$ bundle exec guard
```

**Now enjoy Developing while your browser refreshes after any change**

-----------------------------------

## Note:
If you had any Issues that the changes in **scss** files are not watched.
In **Guardfile** add this line :
```
 # file needing a full reload of the page anyway
  watch(%r{app/assets/stylesheets/.+\.scss})
```

**Make Sure to restart livereload and rails servers , otherwise the changes will not take effect**


------------------------------------------------------

## Locations:

1. Gems we added in [Gemfile](https://github.com/k97-Media/railsAutoReload/blob/39a29dfcf8692118008be663bbb29ee069d55449/Gemfile#L47)
2. Line we added in [Middelware](https://github.com/k97-Media/railsAutoReload/blob/39a29dfcf8692118008be663bbb29ee069d55449/config/environments/development.rb#L82)
3. Line we added in [Guardfile](https://github.com/k97-Media/railsAutoReload/blob/39a29dfcf8692118008be663bbb29ee069d55449/Guardfile#L57)




