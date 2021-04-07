# মেথড এবং প্রোপার্টি

## প্রোপার্টি

কোন ফিচার বা বৈশিষ্ট্য বোঝাতে আমরা প্রোপার্টি ব্যবহার করতে পারি । যেমন: একজন মানুষের উচ্চতা বোঝানোর জন্য আমরা `Person` ক্লাস এ `height` নামে একটি প্রোপার্টি তৈরি করতে পারি ।

প্রোপার্টি গুলোকে সচরাচর ফিল্ড বা এ্যাট্রিবিউট নামেও ডাকা হয় । প্রোপার্টি ডিফাইন করা খুবই সহজ, প্রথমে ভিজিবিলিটি কিওয়ার্ড \(`public`, `protected` কিংবা `private`\) এর যে কোন একটি লিখতে হবে এবং তারপর আমরা যেভাবে ভ্যারিয়েবল ডিক্লেয়ার করি সেভাবেই আমাদের প্রোপার্টি ডিফাইন করবো । ভিজিবিলিটি নিয়ে আমরা পরবর্তীতে কোন চ্যাপ্টারে আলোকপাত করবো । আসুন আমরা দেখে নেই প্রোপার্টি কিভাবে ব্যবহার করা যায়:

```php
<?php

class Person
{
    public $age;
}


$person = new Person();
$person->age = 32;

$anotherPerson = new Person();
$anotherPerson->age = 45;

var_dump($person->age);
var_dump($anotherPerson->age);
```

এখানে আমরা `age` নামে একটি প্রোপার্টি ডিফাইন করলাম । পরবর্তীতে ঐ ক্লাসের দুটো ইনস্ট্যান্স তৈরি করে নিলাম এবং তাদের বয়স সেট করে দিলাম । লক্ষ্য করুন, কোন অবজেক্ট ইনস্ট্যান্স থেকে তার প্রোপার্টি এ্যাক্সেস করার জন্য আমরা `->` সিম্বলটি ব্যবহার করছি । এবং যখন প্রোপার্টি এ্যাক্সেস করছি তখন প্রোপার্টির নামের আগে ভ্যারিয়েবল সাইন নেই । অর্থাৎ, `$person->$age` নয়, বরং `$person->age` এর মাধ্যমে আমরা `age` প্রোপার্টি এ্যাক্সেস করতে পারি ।

এই অপারেটর \(`->`\) টি অবজেক্ট অপারেটর নামে পরিচিত।

যদি আমরা প্রোপার্টির নামের আগে ভ্যারিয়েবল সাইন ব্যবহার করে এ্যাক্সেস করি তখন সেটি ভ্যারিয়েবল ভ্যারিয়েবল এর মত করে কাজ করবে । প্রথমে `$age` এর ভ্যালু বের করে নিয়ে এরপর `$person->(value of $age)` এভাবে কল করা হবে । এভাবে আমরা একটি অবজেক্ট ইন্সট্যান্স থেকে ডাইনামিক্যালি তার প্রোপার্টি এ্যাক্সেস করতে পারি ।

আমরা চাইলে প্রোপার্টির একটি ইনিশিয়াল ভ্যালুও দিয়ে দিতে পারি । তবে এই ইনিশিয়াল ভ্যালু অবশ্যই কন্সট্যান্সট এক্সপ্রেশন হতে হবে \(অর্থাৎ কোন ভ্যারিয়েবল বা ফাংশন ব্যবহার করা চলবে না\) । যে কোন ফিক্সড ভ্যালু \(যেমন: স্ট্রিং বা ইন্টিজার\) কিংবা কোন কনস্ট্যান্ট ব্যবহার করা যেতে পারে ।

```php
<?php
class Person
{
    public $name = "masnun";
}
```

এটাকে প্রোপার্টি ইনিশিয়ালাইজেশন বলা হয় ।

## মেথড

কোন কাজ করার জন্য আমরা মেথড ব্যবহার করি । মেথড আসলে ফাংশন যেটা ক্লাসের ভিতরে থাকে এবং ঐ ক্লাসের সকল প্রোপার্টি এবং মেথড এ্যাক্সেস করতে পারে ।

মেথড এর একটা উদাহরন দেখি:

```php
<?php

class Person
{
    public $age;

    public function getAge()
    {
        return $this->age;
    }
}


$person = new Person();
$person->age = 32;

$anotherPerson = new Person();
$anotherPerson->age = 45;

var_dump($person->getAge());
var_dump($anotherPerson->getAge());
```

এখানে আমরা `getAge()` নামে একটি মেথড ডিফাইন করেছি যেটার কাজই হচ্ছে ঐ অবজেক্ট ইন্সট্যান্স এর `age` প্রোপার্টির ভ্যালু রিটার্ন করা ।

আমরা দেখলাম `$this` এই ভ্যারিয়েবলটির মাধ্যমে আমরা ঐ অবজেক্ট ইনস্ট্যান্সটি এ্যাক্সেস করেছি । এটি সম্পর্কে আমরা আরো বিস্তারিত জানবো "স্ট্যাটিক ও নন-স্ট্যাটিক কনটেক্সট" সেকশনে । আপাতত আমাদের মনে রাখতে হবে `$this` ভ্যারিয়েবলটি যে ক্লাসে ব্যবহার করা হয়, এটি তার প্রত্যেকটি ইনস্ট্যান্সে নিজ নিজ ইনস্ট্যান্স কে পয়েন্ট করে ।
