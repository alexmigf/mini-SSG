# Mini SSG [Alpha]
Simple static site generator, to prevent you write DRY HTML files with minimal syntax  
Built with Nodejs  
Inspired by Laravel Blade Template and Sergey.cool SSG

## Use Case
For someone who works with a lot of html files and many reuse components (header, footer, etc.) or want to use general layout

## Why and How to use it
Check out [mini SSG website](https://minissg.vercel.app)

## Syntax preview

Import page
```
@import(header)		

<p>Your awesome content</p>

@import(footer)
```

Use general layout
```
@layout(base) 

@section(title, Your Page Title)

@section
<main>
	Hey.. meet your awesome content
</main>
@endsection
```

How layout looks like
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>@attach(title)</title> <!-- render your title above -->
</head>
<body>
	@attach(section) <!-- render everything from section above -->
</body>
</html>
```

Layout can include multiple imports
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>@attach(title)</title> <!-- render your title above -->
</head>
<body>
	@import(header)
	@attach(section) <!-- render everything from section above -->
	@import(footer)
</body>
</html>
```

Need components? don't worry!
```

<h2>Other stuff</h2>

@component(story)
	@slot(fullDiv)
		<p>😀 I'm slot with name text</p>
		<p>I can be very complex element</p>
	@endslot

	@slot(textOnly)
		I can also be just text like this
	@endslot
@endcomponent
```

How your component looks like
```
<div>
	<div class="flex is-space-around">
		<div class="someClass">
			@attach(fullDiv)
		</div>

		<p>@attach(textOnly)</p>
	</div>	
</div>
```

If attach need a default value as fallback
```
<title>@attach(title, My default title)</title>
```

That't it learn more at [mini SSG website](https://minissg.vercel.app/tour)