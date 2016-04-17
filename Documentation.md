# Overview #
This jQuery plugin will allow you to limit input into form fields. It can display a message as the user types to let them know how many characters they have remaining.

# Use #
[jQuery](http://jquery.com) is required to use this plugin.

## Examples ##
Limit all textareas to the default limit of 255 characters:
```
$(function() {
	$('textarea').inputlimiter();
});
```
Specify a limit or 100 characters:
```
$(function() {
	$('textarea').inputlimiter({limit: 100});
});
```
More advanced examples can be found on the [demonstration](http://rustyjeans.com/jquery-inputlimiter/demo.htm) page.

# Options #
## limit ##
Type: Integer

Default: `255`

Controls how many characters the Input Limiter will allow the user to type into the field it is attached to. Once the limit is reached the user's input will be truncated.

## boxAttach ##
Type: Boolean

Default: `true`

Determines whether the box containing the Input Limiter remText and limitText will attach itself to the bottom the field that is in focus.

## boxId ##
Type: String

Default: 'limiterBox'

Determines the id that will be assigned to the box that will display the remText and limitText.

## boxClass ##
Type: String

Default: 'limiterBox'

Determines the class that will be attached to the box (boxId) that will display the remText and limitText.

## remText ##
Type: String

Default: '%n character%s remaining.'

This string displayed the remaining characters. It will be updated as the user types into the input. Using the default remTextFilter; %n will be replaced with the number of characters remaining, %s a plural 's'. The %s will be replaced by the letter 's' except when %n is equals to 1, then %s will return nothing. If zeroPlural is set to false this will also return nothing when %n is equal to 0.

## remTextFilter ##
Type: Function

Default:
```
function (opts, charsRemaining) {
	var remText = opts.remText;
	if (charsRemaining === 0 && opts.remFullText !== null) {
		remText = opts.remFullText;
	}
	remText = remText.replace(/\%n/g, charsRemaining);
	remText = remText.replace(/\%s/g, (opts.zeroPlural ? (charsRemaining === 1 ? '' : 's') : (charsRemaining <= 1 ? '' : 's')));
	return remText;
};
```

This function gets two arguments passed to it: the options, and the remaining characters. By Default this function replaces '%n' with the characters remaining and '%s' with the letter 's' when charsRemaining is anything but '1'.

## remTextHideOnBlur ##
Type: Boolean

Default: `true`

Controls whether the remText is displayed after the input loses focus. The limitText will still be displayed. This option only applies if attachBox is false, otherwise the boxId will be hidden when the field loses focus.

## remFullText ##
Type: String

Default: `null`

This string is displayed when the remaining characters is equals to zero. If this string is null remText will be displayed.

## limitTextShow ##
Type: Boolean

Default: `true`

Determines whether the limitText will be displayed after the remText.

## limitText ##
Type: String

Default: 'Field limited to %n character%s.'

Text that informs the user about the limit. Using the default limitTextFilter; %n will be replaced with the number of characters thje field is limited to, %s adds a plural 's'. The %s will be replaced by the letter 's' except when %n is equals to 1, then %s will return nothing.

## limitTextFilter ##
Type: Function

Default:
```
function (opts) {
	var limitText = opts.limitText;
	limitText = limitText.replace(/\%n/g, opts.limit);
	limitText = limitText.replace(/\%s/g, ( opts.limit == 1?'':'s' ));
	return limitText;
};
```

This function gets one argument passed to it: the options. By Default this function replaces '%n' with the limit and '%s' with the letter 's' when the limit is anything but '1'.

## zeroPlural ##
Type: Boolean

Default: `true`

Determines if the '%s' will be populated with the letter 's' when the characters remaining is equal to zero. If this is true '%s' with be populated with an 's' when the remaiing character is equal to zero. If this option is false the '%s' will not be populated when the remaining characters is equal to zero.

## allowExceed ##
Type: Boolean

Default: `false`

Determines whether the user is allow to keep entering more characters after they have reached the limit. By default the option stops the user from typing when they reach the limit. When the limited is exceeded the remaining text will display a negative number indicating how many character they are over.

## useMaxlength ##
Type: Boolean

Default: `true`

If this option is set to true the `maxlength` attribute of the element will be used. If a limit is specified in the options the limit passed will override the `maxlength` attribute. If no `limit` option is passed it will use the limit from the `maxlength` attribute.

## limitBy ##
Type: String

Default: `'characters'`

Gives you the ability to limit a field either by characters or by words. The only valid values for this option are `'characters'` and `'words'`.

## lineReturnCount ##
Type: Integer

Default: `1`

This gives you the ability to count new lines as more than one character. If your system is storing a new line as two characters in your database you can use this option, by setting `lineReturnCount` to `2` it will count all line returns as two characters.