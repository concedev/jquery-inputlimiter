This jQuery plugin will allow you to limit input into form fields. It can display a message as the user types to let them know how many characters/words they have remaining.

This is my first attempt at creating a jQuery Plugin, please feel free to give me advice. :)

The Input Limtier 1.3.1 adds option to count line returns as two (or more) characters. The new option is: lineReturnCount, and the value defaults to 1. If your system is storing a new line as two charaters in your database you can use this new option, by setting lineReturnCount to 2 it will count all line returns as two characters.

The Input Limiter 1.3 release fixes a few bugs and adds the new features: useMaxlength which allows you to leave off the limit option and the plugin will display the remaining text info based on the fields maxlength attribute, this option is on by default. Also added limitBy option which allows you to limit the field based on either characters or words.

The Input Limiter 1.2.2 release adds a new options: allowExceed. This option allows you to let the user continue typing after they have reached the limit. Also in this version is a fix for a problem where you could add new lines to a textarea after the limit was reached by pressing enter/return.

I’ve release version Input Limiter 1.2.1 which fixes a small bug. The bug had to do with dynamically changing the limit on an input, when you changed the limit to a longer limit the previous (shorter) limit stayed attached to the input.

The Input Limiter 1.2 release adds two new options: remFullText and zeroPlural. These options allow you to custom the remaining text message when no characters are remaining.

Input Limiter 1.1 release allows you to completely customize the text that is output. Two new options: remTextFilter and limitTextFilter allow you to do anything you want to the output text before it is displayed.