
================
global vs local
================

So far we've used ``set`` to define variables. By default ``set`` defines a global variable, this means that once the variable has been set you'll be able to use that variable whenever you want while the script is running. When you define a local variable the variable only exists in the 'scope' it is in. The scope is the code between curly brackets. Here is an example: ::

  print "main script level".
  if 1 = 1 {
    print "first level of curly brackets".
    if 1 = 1 {
      print "second level of curly brackets".
      if 1 = 1 {
        print "third level of curly brackets".
      }
      if 1 = 1 {
        print "fourth level of curly brackets".
      }
    }
  }

Using ``local`` in curly brackets the variable will only exists within the curly brackets block, here is an example: ::

  set var1 to 5.

  if 1 = 1 {
    local var1 is 10.
    local var2 is 100.
    print var1. // shows 10
  }

  print var1. // shows 5 because var1 within the curly brackets doesnt exists anymore
  print var2. // shows an error message because var2 doesnt exists outside of the curly brackets

The same goes for multiple levels of brackets: ::

  if 1 = 1 {
    local var1 is 5.

    if 1 = 1 {
      local var1 is 10.
      local var2 is 100.
      print var1. // shows 10
    }

    print var1. // shows 5
    print var2. // shows an error message because var2 doesnt exists outside of the curly brackets
  }

As you can see there are two versions of ``var1`` because you've used ``local``. Using ``set`` on an existing variable will change the variable and wont create a separate variable. ::

  local var1 is 5.

  if 1 = 1 {
    set var1 to 10.
  }

  print var1. // shows 10

If you want to create a variable that will be accessible outside of a curly brackets block you can use ``global``, globals **DO NOT** override previously set locals. ::

  local var1 is 5.

  if 1 = 1 {
    global var1 is 10.
    global var2 is 100.
  }

  print var1. // shows 5
  print var2. // shows 100


















.
