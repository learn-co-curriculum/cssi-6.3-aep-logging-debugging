---
tags: cssi, gae, python, logging, debugging, console
level: 2
languages: python
---

#Google App Engine: Logging and Debugging

#Objectives:

+ How to find and fix errors by reading the App Engine log console
+ Understanding the mindset debugging and use tools for debugging

#Motivation
ITS NOT WORKING! It can be very frustrating when your web application is not running the way it's supposed to. But have no fear! We not only learn from errors but we are instructed by them!
One of the most important things you'll need to know is how to find and fix bugs in your app. App Engine has a log console that shows you the raw output of the Python code, plus other things you may want to log.

#Lesson: Debugging
**Code Along!**
+ Add an error to your python script in your helloworld.py file, something like...

```python
print 'Content-Type: text/plain'
print ''
print 'Hello, world!' - 8
```
Save then Reload the page. You should either see an HTTP 500 Server Error or your page might just be blank. This happens if your script cannot run successfully.

##The Mindset of Debugging
<img src="http://collectskin.com/wp-content/uploads/2010/07/killbug.png" width="300px">

You’ve been working hard on your code and you run your application. And then you see...**AN ERROR MESSAGE**. Breathe. Don’t panic. Ignore all thoughts of doom. The process of writing code is the process of debugging. As a programmer, you will always be looking for bugs to fix. Have no fear! Your error message is actually a message that’s pointing you to your next step.

+ In your GoogleAppEngineLauncher window, press the **Logs** button. The Log Console window will open up. You should see your error message for the script you just wrote.

+ Find the error line. This gives you a stack trace, just like errors in normal Python programs. In larger programs, you'll typically see much more information, but you should look for three things specifically:

<kbd style="color:red">ERROR    2015-06-17 22:19:45,960 cgi.py:122] Traceback (most recent call last):</br>
  File "/Users/Development/appengine_practice/helloworld.py", line 6, in module</br>
    print 'Hello, world!' - 8</br>
TypeError: cannot concatenate 'str' and 'int' objects</kbd>

+ The name of the file that where the error happened, in this case helloworld.py
+ The line number of the error in this case the error in line 6.These two pieces of info give you a pretty good hint as to where you should look.
+ The actual error, in this case a TypeError caused by trying to concatenate str and int objects. (cannot concatenate 'str' and 'int' objects)


+ Fix the error and reload the page.

You will become very comfortable checking the logs and finding errors: you will probably be doing lots of this as you write your apps. The quicker you are at tracking down bugs, the less time you'll spend debugging and the more time you can spend building awesome apps.


#Partner Programming Exercise 1:
Copy and paste the following into helloworld.py. It contains a couple errors! Use the console to find and fix the errors.

```python
print 'Content-Type: text/plain'
print ''
if true:
  print 'The truth will set you free.'
else
  print 'How did I get here?'
```

#Partner Programming Exercise 2:

Partner Exercise 2: This longer program contains more than one error. Use the console to help you track them down, and fix them all.
```python
def TalkLikeAPirate(sentence):
  """Converts a sentence to pirate-speak. Adapted from Python 3 for Absolute Beginners: http://www.google.com/books?id=sQGFIX_0xCUC&pg=PA242"""
  # Strip whitespace and punctuation
  sentence = sentence.strip().rstrip('.!')
  # Lowercase the first letter of the sentence
  sentence = sentence[0].lower() + sentence[1:]
  # Piratify the text
  sentence = 'Yarr, ' + sentance + ', me hearties!'
  retunn sentence

print 'Content-Type: text/plain'
print ''
sentence = 'Hello, world!'
print TalkLikeAPIrate(sentence)
```

#Lesson: Logging
Logging is a means of tracking events that happen when a program runs.The logging module lets you write messages directly to the console instead of sending them to the browser.

1. Open up your terminal and open up your helloworld.py in Atom.

2. Import the logging module. We can add this line to the top of your script:  <kbd>import logging</kbd>

3. Add a logging statement:
```python
logging.info('Hello, logs!')
```
4. Reload the page and check the log console to find your message!!

#Partner Programming Logging Exercise 1:
Try copy and pasting this script into helloworld.py:
```python
import logging

def IsPrime(n):
  """A simple (but inefficient) check to see whether a number is prime."""
  for possible_factor in range(1, n):
    if n % possible_factor == 0:
      return False

  return True

print 'Content-Type: text/plain'
print ''

n = 100
if IsPrime(n):
  print '%d is prime' % n
else:
  print '%d is not prime' % n
```
Change n to a couple different numbers. Notice that it never thinks a number is prime, even when it should. What's the problem here?

These kinds of bugs can be tricky to track down. Fortunately, logging can help you figure out exactly why it doesn't think any numbers are prime.

+ Add a logging statement in the for loop:
```python
for possible_factor in range(1, n):
  if n % possible_factor == 0:
    logging.info('Found a factor: %d', possible_factor)
    return False
```
Now try reloading the page with a different number. Check the logs: do you see the problem? How can you fix it?

#Conclusion

Patience young grasshopper. Debugging can be frustrating but you have tools that can help you fix errors in your code. Read your error messages in the console to find your next step. Use the PEP protocol. Ask for help!

#Labs:

(to add)
