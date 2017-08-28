---
layout: post
title:  Time, Datetime, Weekday query to find records
date:   2017-03-17 16:40:16
description: Time, Datetime, Weekday query to find records [ruby][ruby-on-rails]
---

# Find records between time of the day (not date only time)

It's quite straightforward to find records between two datetime. But it would be little tricky to find records between two *time*, only time not datetime.
We can write it that way:
 
{% highlight ruby %}
Task.where([":date_time >= start_time::time AND :date_time <= end_time::time", { date_time: DateTime.current.strftime('%H:%M:%S') }])
{% endhighlight %}

# Find records of specific weekday

Say, you want to find record only which are created on Monday, so write query like this:

{% highlight ruby %}
Task.where([":wday = ANY (days_of_the_week)", { wday: Date.current.strftime('%A') }])
{% endhighlight %}
