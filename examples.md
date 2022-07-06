# Examples

## Callbacks example <a href="#callbacks-example" id="callbacks-example"></a>

`paint` - callback

```
ui.set_callback("paint", function()
 -- draw something
end)
```

`createmove` - callback

```
ui.set_callback("createmove", function()
  -- do something
end)
```

## Manipulation of the panorama <a href="#manipulation-of-the-panorama" id="manipulation-of-the-panorama"></a>

Download this library, and put it next to the lua. - [download](https://discord.com/channels/863692583284637736/994314038165110874/994314627536125952)&#x20;

**Libraries stored in 'Counter-Strike Global Offensive\lua\\'**



```
local js = require("lib")

js.eval([[
    mainMenuSpinbot = undefined
    mainMenuRainbow = undefined
    vanityPanel.SetDirectionalLightAmount(0);
]])

js.eval([[
    var vanityPanel = $.GetContextPanel().GetChild(0).FindChildInLayoutFile( 'JsMainmenu_Vanity' );

    var menuSpinbotDegrees = 0;
    var menuSpinbotSpeed = 1

    function mainMenuSpinbot() {
        menuSpinbotDegrees += menuSpinbotSpeed / 10;

        if (menuSpinbotDegrees > 360) {
            menuSpinbotDegrees = menuSpinbotDegrees - 360;
        }

        vanityPanel.SetSceneAngles(0, menuSpinbotDegrees, 0, 0)

        $.Schedule(0.01, mainMenuSpinbot)
    }

    var mainMenuRainbowEnabled = false;
    var rainbowSpeed = 0;
    var r = 0.0;
    var g = 0.0;
    var b = 0.0;
    var x = 0.0;
    var y = 0.0;

    function mainMenuRainbow() {
        if (rainbowSpeed > 0) {
            if( y >= 0 && y < 255 ) {
                r = 255;
                g = 0;
                b = x;
            } else if( y >= 255 && y < 510 ) {
                r = 255 - x;
                g = 0;
                b = 255;
            } else if( y >= 510 && y < 765 ) {
                r = 0;
                g = x;
                b = 255;
            } else if( y >= 765 && y < 1020 ) {
                r = 0;
                g = 255;
                b = 255 - x;
            } else if( y >= 1020 && y < 1275 ) {
                r = x;
                g = 255;
                b = 0;
            } else if( y >= 1275 && y < 1530 ) {
                r = 255;
                g = 255 - x;
                b = 0;
            }

            x+=rainbowSpeed;
            if( x >= 255 )
                x = 0;

            y+=rainbowSpeed;
            if( y > 1530 ) {
                y = 0;
            }

            vanityPanel.SetAmbientLightColor(r, g, b);
        }
        $.Schedule(0.01, mainMenuRainbow)
    }

    mainMenuRainbow();
    mainMenuSpinbot();
]])

js.eval([[menuSpinbotSpeed = 50;]])
js.eval([[rainbowSpeed  = 1;]])
```

## Find signature <a href="#find-signature" id="find-signature"></a>

```
local render_beams_signature = "B9 ? ? ? ? A1 ? ? ? ? FF 10 A1 ? ? ? ? B9"
local match = utils.find_signature("client.dll", render_beams_signature)
```
