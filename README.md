# Dream Cheeky

Make your Dream Cheeky USB Device do something cool.

World, the time has come to PUSH THE BUTTON!

## Support
The following Dream Cheeky USB Devices are supported `(vendor_id:product_id)`

Big Red Button ``(1d34:000d)``
Big Red Button (Iron Man Edition) ``(1d34:0008)``
USB Fidget ``(1d34:0001)``  

Please get in touch if you have an unsupported Dream Cheeky device.

## Usage

Simple:

```ruby
require 'rubygems'
require 'dream_cheeky'

DreamCheeky::UsbFidget.run do
  push do
    `say "BEEP!"`
  end
end
```

Advanced:

```ruby
require 'rubygems'
require 'dream_cheeky'
require 'watir-webdriver'

DreamCheeky::BigRedButton.run do
  browser = Watir::Browser.new

  open do
    browser.goto 'devastatingexplosions.com'
  end

  close do
    browser.close
  end

  push do
    browser.object(:id => 'flashcontent').click
  end
end
```

## Requirements

1. A supported Dream Cheeky USB Device. Example: http://dreamcheeky.com/big-red-button

2. Mac OS X with Developer Tools installed or Linux with libusb and udev installed.

3. On Linux you may have to 
   [add a udev rule](http://reactivated.net/writing_udev_rules.html). To do that,
   create a file named 99-dream_cheeky.rules with the following content:
   
        SUBSYSTEM=="usb", ATTRS{idVendor}=="1d34", ATTRS{idProduct}=="000d", MODE="0666", GROUP="plugdev"
   
   Then, copy the file to /etc/udev/rules.d/99-dream_cheeky.rules (you probably would 
   need root priviles to copy it).

## Maintainers

* Derrick Spell (https://github.com/derrick)

## Contributors

* Gustavo Armagno (http://github.com/gusaaaaa) added Linux support - many thanks!
* Matt Sephton (http://github.com/gingerbeardman) added the UsbFidget class.

