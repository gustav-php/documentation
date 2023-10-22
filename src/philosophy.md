# Philosophy

Hi, I'm [Torsten](https://github.com/TorstenDittmann) and like to code. I'm not here to sell you on the next big thing, but rather to share my opinion about current PHP frameworks and why I wanna do things a little differently.

## The Overwhelming Maze

I guess many developers have been in these shoes, navigating the maze of PHP frameworks. Complex libraries, random features, inscrutable terminology and the feeling that the kitchen sink got thrown in for good measure. It can be a confusing landscape.

The big players like [Laravel](https://laravel.com) and [Symfony](https://symfony.com) are awesome, no doubt.

But lack developer experience, I think Laravel especially does a really bad job at it. In my opinion, I should be able to navigate and discover the namespaces and classes of my framework by simply following common sense and known naming patterns. 

After 1 minute with Laravel you will encounter a wild `Illuminate\Support\Facades\Route` class and this is only the beginning. How does all those terms lead me to creating a `Route` for my "Hello World!" endpoint. It's ecosystem is filled with terms like `Illuminate`, `Eloquent` and `Artisan` that just add an unncessecary layer of complexity.

Once you you learned the characteristic of Laravel, Symfony and co, you can build whatever you want at _enterprise_ level. 

But what if your project isn't an enterprise monolith? What if you want simplicity?

## Simplicity

I want to keep it lean. I rather give you a blank canvas and let you paint your project the way you want. No feature bloat, no complexity - just the tools you need.

Have you ever opened a framework's project scaffold only to find it sprouting 15 folders and more files than you can count? It's a recipe for overwhelm. GustavPHP starts you off with a clean slate, not a tangled mess of directories.

That also means, that this framework will not be the swiss knife for all your needs. I don't see this framework ever being shipped with an ORM because, honestly, there are some fantastic options available and therefore rather support you in implementing whatever you feel the most comfortable with.

## No Magic

We all enjoy a little magic, but not when it leaves us in the dark. Some frameworks operate with a touch of 'magic' that can make your codebase feel like a mystery. Probably why Ruby on Rails never hooked me. I value transparency and control. Your code should be a friend, not a stranger.

## Type safety

One aspect that's been missing from many PHP frameworks is robust type safety. The recent PHP versions, especially PHP 7.0 and beyond, have made significant improvements in enhancing type hinting and type declarations. 

However, not all frameworks fully embrace these advancements. 

Having to define some `random-string` on a setter method just to pass `random-string` again in a getter method somewhere else with a `mixed` return type tires me. 

I want to design GustavPHP with type safety in mind, offering a codebase that benefits from strong type hinting, enabling you to catch errors at compile-time rather than at runtime. This ensures a more reliable and maintainable codebase.

## Modern PHP

Remember when you were stuck with whatever PHP version your hosting provider decided to throw your way? Those days are luckily over. With containerization tools like Docker, you get to call the shots.

In recent releases the language has undergone a remarkable transformation, introducing features like [Just-in-Time Compilation](https://php.watch/versions/8.0/JIT), [Fibers](https://php.watch/versions/8.1/fibers), [Match Expressions](https://php.watch/versions/8.0/match-expression), [Attributes](https://php.watch/articles/php-attributes), and a plethora of performance enhancements, making it a modern and powerful choice for web developers.

But it feels like the ecosystem is not ready yet - remembering that there are some popular libraries being stuck supporting legacy version like PHP 5.6 and just cannot take advantage of the newest additions.

## Final

GustavPHP isn't just a framework; it's my personal take on PHP as a developer, and I'm excited to share it with you. I wanna keep things simple, giving you control, and embracing the modern PHP world. It's your project, and I'm here to help you make it shine.
