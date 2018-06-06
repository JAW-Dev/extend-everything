# Extend Everything (Sass)

This is a silly little exercise for creating a way to automatically add Sass @extend(s) right in your selectors without the need to keep track of your @extend(s).

### !!!WARNING!!!
This is just an experiment and I do not recommend you using this in a live production environment. Overuse of the Sass @extend is bad practice and can really mess up your CSS if you let it get out of hand. Again, I do not recommend you use this and I take no responsibility if you do choose to use Extend Everything in a live production environment.

This hasn't been fully tested and is probably buggy as all hell. If you find any errors feel free to submit an issue and/or submit a pull request. I may or may not respond. As I said, this was just an experiment and as of right now I don't really intend to develop this any further unless there is an overwhelming interest. Which is unlikely.

You have been warned.

## Usage
Import the `_extend-everything.scss` file in you Sass pipline.

Use the following example's format to create an @extend your CSS properites.

`@include extend-property("your-property", the-property-value);`

## Example

```
.selector1 {
	@include extend-property("position", relative);
	@include extend-property("padding", 10rem);
	@include extend-property("margin", 1rem 2rem);
	@include extend-property("background", #CCCCCC);
	@include extend-property("background", #CCCCCC url("./images/test.jpg") no-repeat);
	@include extend-property("content", "Testcontent");
}

.selector2 {
	@include extend-property("position", relative);
	@include extend-property("padding", 10rem);
	@include extend-property("margin", 1rem 2rem);
}

.selector3 {
	@include extend-property("background", #CCCCCC);
	@include extend-property("background", #CCCCCC url("./images/test.jpg") no-repeat);
	@include extend-property("content", "Testcontent");
}

.selector4 {
	@include extend-property("position", relative);
	@include extend-property("padding", 10rem);
	@include extend-property("margin", 1rem 2rem);
	@include extend-property("background", #CCCCCC);
	@include extend-property("background", #CCCCCC url("./images/test.jpg") no-repeat);
	@include extend-property("content", "Testcontent");
}
```

Will be compiled in your CSS output like this.

```
.selector1, .selector2, .selector4 {
  position: relative;
}

.selector1, .selector2, .selector4 {
  padding: 10rem;
}

.selector1, .selector2, .selector4 {
  margin: 1rem 2rem;
}

.selector1, .selector3, .selector4 {
  background: #CCCCCC;
}

.selector1, .selector3, .selector4 {
  background: #CCCCCC url("./images/test.jpg") no-repeat;
}

.selector1, .selector3, .selector4 {
  content: "Testcontent";
}
```
