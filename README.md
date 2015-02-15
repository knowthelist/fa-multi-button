fa-multi-button
========

Modern toggle, push button or just a signal indicator

![](http://knowthelist.github.io/fa-multi-button/fa-multibutton-example.png)
Features
-------
* Create toggle buttons with font awesome icons
* Create push buttons with glow off effect
* Create read only buttons as an indicator control

Usage
-------
<code>$(selector).famultibutton(options);</code>

Examples
-------

```html
<div id="btn1"></div>

<script>
    $(function() {
        btn = $('#btn1').famultibutton();
		btn.setOn();
    });
</script>
```
[More examples with fa-multi-button](http://knowthelist.github.io/fa-multi-button)

Options
-------

- **icon**: The foreground font awesome icon name (default: 'fa-power-off')
- **backgroundIcon**: The background font awesome icon name (default: 'fa-circle')
- **offColor**: Color of the foreground in state off (default: '#2A2A2A')
- **offBackgroundColor**: Color of the foreground in state off  (default: '#505050')
- **onColor**: Color of the foreground in state on  (default: '#2A2A2A')
- **onBackgroundColor**: Color of the background in state on (default: '#aa6900')
- **classes**: Array of optional font awesome classes to add to selector (default: 'fa-3x')
- **mode**: Sets the kind of button: 'toggle', 'push' or 'signal' (default='toggle')
- **toggleOn**: Function called in state on
- **toggleOff**: Function called in state off

[See the list for all available icons](http://fortawesome.github.io/Font-Awesome/icons)

Dont forget the 'fa-' suffix in icon and backgroundIcon name.

Hooks
-------

```html
<script>
	$('.button').famultibutton({
		icon: 'fa-lock',
		onColor: '#ffffff',
		offColor: '#ffffff',
		onBackgroundColor: '#33dd00',
		toggleOn: function( ) { /*make something*/ },
		toggleOff: function( ) { /*make something*/ }
	});
</script>
```

Update call for multi instances
-------

```html
<div class="button" device="mylamp"></div>
<div class="button" device="otherlamp"></div>

<script>

// init buttons
 $('.button').each(function(index) {
 	
 	var device = $(this).attr('device');
 	var elem = $(this).famultibutton({
		icon: 'fa-lightbulb-o',
		backgroundIcon: 'fa-circle',
		offColor: '#2A2A2A',
		onColor: '#2A2A2A',
		// Called in toggle on state.
		toggleOn: function( ) { setSomething( device,"on" ); },
	   	toggleOff: function( ) { setSomething( device,"off" ); },
	});
	// store instance into data
	elem.data('famultibutton',elem);
 });
 
 // update buttons
 function doUpdate() {
 	$('.button').each(function(index) {
 	  var state = getSomething( $(this).attr('device') );
	  if ( state == 'on' )
		$(this).data('famultibutton').setOn();
	  else
		$(this).data('famultibutton').setOff();
 	});
 }
</script>
```

License
-------
This project is licensed under [MIT](http://www.opensource.org/licenses/mit-license.php).
