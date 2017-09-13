<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js">

</script>

<script type="text/javascript">

	function UpdateTableHeaders() {
		 $("div.divTableWithFloatingHeader").each(function() {
		     var originalHeaderRow = $(".tableFloatingHeaderOriginal", this);
		     var floatingHeaderRow = $(".tableFloatingHeader", this);
		     var offset = $(this).offset();
		     var scrollTop = $(window).scrollTop();
		     if ((scrollTop > offset.top) && (scrollTop < offset.top + $(this).height())) {
		         floatingHeaderRow.css("visibility", "visible");
		         floatingHeaderRow.css("top", Math.min(scrollTop - offset.top, $(this).height() - floatingHeaderRow.height()) + "px");

		         // Copy cell widths from original header
		         $("th", floatingHeaderRow).each(function(index) {
		             var cellWidth = $("th", originalHeaderRow).eq(index).css('width');
		             $(this).css('width', cellWidth);
		         });

		         // Copy row width from whole table
		         floatingHeaderRow.css("width", $(this).css("width"));
		     }
		     else {
		         floatingHeaderRow.css("visibility", "hidden");
		         floatingHeaderRow.css("top", "0px");
		     }
		 });
	}

	$(document).ready(function() {
		 $("table").each(function() {
		     $(this).wrap("<div class=\"divTableWithFloatingHeader\" style=\"position:relative\"></div>");

		     var originalHeaderRow = $("tr:first", this)
		     originalHeaderRow.before(originalHeaderRow.clone());
		     var clonedHeaderRow = $("tr:first", this)

		     clonedHeaderRow.addClass("tableFloatingHeader");
		     clonedHeaderRow.css("position", "absolute");
		     clonedHeaderRow.css("top", "0px");
		     clonedHeaderRow.css("left", $(this).css("margin-left"));
		     clonedHeaderRow.css("visibility", "hidden");

		     originalHeaderRow.addClass("tableFloatingHeaderOriginal");
		 });
		 UpdateTableHeaders();
		 $(window).scroll(UpdateTableHeaders);
		 $(window).resize(UpdateTableHeaders);
	});

</script>

It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to JHelp!](http://www.jhelp.fr)

# This is an <h1> tag

## This is an <h2> tag

###### This is an <h6> tag



Header1 | Header2
--------|--------
Content 1.1 | Content 2.1
Content 1.2 | Content 2.2
Content 1.3 | Content 2.3
Content 1.4 | Content 2.4
Content 1.5 | Content 2.5
Content 1.6 | Content 2.6
Content 1.7 | Content 2.7
Content 1.8 | Content 2.8
Content 1.9 | Content 2.9




*This text will be italic*
_This will also be italic_

**This text will be bold**
__This will also be bold__

_You **can** combine them_



* Item 1
* Item 2
  * Item 2a
  * Item 2b

1. Item 1
1. Item 2
1. Item 3
   1. Item 3a
   1. Item 3b

```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```

```java
import jhelp.util.debug.Debug;

public static void main(String[] args)
{
	Debug.information("This is an information");
}
```




