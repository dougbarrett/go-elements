# go-elements

go-elements is a templ powered component library for Go.

**This project is heavily under development and is not in a usable state**


## What does this do?

go-elements was born out of the want for a fast way to build interfaces for apps quickly, so it allows you to take code like this:

```templ
package main

import l "github.com/dougbarrett/go-elements/components/layout"

func nav(currentItem string) []l.NavItem {
	return []l.NavItem{
		l.NewNavItem("Home", "/").
			IsActive(currentItem == "home"),
		l.NewNavItem("About", "/about").
			IsActive(currentItem == "about"),
		l.NewNavItem("Contact", "/contact").
			IsActive(currentItem == "contact"),
	}
}

func base(page string) l.Base {
	return l.NewBase().SetNavItems(
		nav(page)...,
	)
}

templ Homepage() {
	@base("home").SetPageTitle("Welcome to the homepage").R() {
		<p>This is the homepage of the website.</p>
		<p>Adding some more content to the page.</p>
	}
}

templ About() {
	@base("about").SetPageTitle("About").R() {
		<p>This is the about page of the website.</p>
		<p>Adding some more content to the page.</p>
	}
}

templ Contact() {
	@base("contact").SetPageTitle("Contact").R() {
		<p>This is the contact page of the website.</p>
		<p>Adding some more content to the page.</p>
	}
}
```

and turn it into this...

![Get this](screenshot-1.png)