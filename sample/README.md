
# sample

This is a small web application that demonstrates the basic use of the
Kiln in a RESTful environment. When run, it displays an utterly
primitive message board. To logon, enter any name and matching
password; e.g., "fred" "fred" will log you in as fred, "mary" "mary"
as mary. Trying "fred" with a password of "bob" will fail. Guess what
"admin" "admin" does?

Once logged in, the application allows you to post messages. Then you
read messages other have posted. You can edit your own messages. The
admin can edit anyone's. You cannot delete.

The code is written in a manner that is (I hope) easy to read and
follow. I have used `(declare ...)` aggressively, and the files should
be in a logical order for learning.

Coding with the Kiln is very different from a functional based
approach. In a way, you have to reverse your thinking. Instead of
saying, "I am here. I have this data. What must I do?" you should say,
"I need these values to build my result. I will list them and figure
them out later."

In your application, the various high-level concepts and artifacts
should each have a unique top-level clay. So there should be a
`current-user` clay and a `current-page-id` clay. The point is this:
clays are not functions that compute a result from arguments. (They
can be, but that is bad Kiln design.)  They are *values*, and they
know how to compute themselves.

The trickiest part of this code, in my opinion, is the dispatcher: it
works backward! In a normal dispatcher, you break apart the request,
get the data from it, and then call the business logic code with that
data. In a Kiln dispatcher, you break apart the request, but only to
provide data which will be used elsewhere. The dispatcher returns
clays that will do the work, but it does not evaluate them.

In short, the dispatcher calls no code. It *chooses* the code, and
sets up the environment where that code will run.

I suggest you begin reading this code in the `sample.request`
module. As you proceed, you will want to refer to `sample.dispatcher`
to learn how they interact. The login logic (which is completely
idiotic) lives in the `sample.logon-logoff` module. There are two
messsage modules, one that holds the message based clays, the other
the underlying "database" code.

Enjoy the Kiln! Please let me know your experience.

straszheimjeffrey@gmail.com

## Usage

Checkout this code from Github. It can be run directly from the
command line if you have lein ring installed. Or else you can evaluate
the sample.repl module and run `(start-server)` from there.

## License

Copyright (C) 2012 Jeffrey Straszheim

Distributed under the Eclipse Public License, the same as Clojure.
