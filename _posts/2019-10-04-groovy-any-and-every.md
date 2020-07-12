---
layout: post
title: Groovy any() and every()
tags: tech groovy java
---

While writing a feature in one of the services in my current company, found a very nifty Groovy function.

I needed to check for a set of invalid keywords from another set. Before lambdas, we’d do something like this:

{% highlight java %}
boolean containsInvalidKeywords(List stringToCheckList) {
     for (String stringToCheck : stringToCheckList) {
         for (String invalidKeyword : invalidKeywordList) {
             if (stringToCheck.toLowerCase().contains(invalidKeyword.toLowerCase())) {
                 return true;
             }
         }
     }
     return false;
 }
{% endhighlight %}

With lambdas, we can do the above snippet as a one-liner:

{% highlight java %}
boolean containsInvalidKeywords(List stringToCheckList) {
    return stringToCheckList.stream().anyMatch(
        stringToCheck -> invalidKeywordList.stream().anyMatch(
            invalidKeyword -> stringToCheck.toLowerCase().contains(invalidKeyword.toLowerCase())
        )
    );
}
{% endhighlight %}

Short, and simple! But with groovy, it’s even simpler!

{% highlight java %}
def containsInvalidKeywords(def stringToCheckList) {
    return stringToCheckList.toLowerCase().any{ 
        stringToCheck -> invalidKeywordList.toLowerCase().any { 
            invalidKeyword -> stringToCheck.contains(invalidKeyword as CharSequence)
        }
    }
}
{% endhighlight %}

Which one do you think is easier?