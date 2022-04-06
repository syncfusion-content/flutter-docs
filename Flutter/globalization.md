---
layout: post
title: Applying Localizations for Syncfusion Flutter widgets
description: This section explains about applying the localization for the applicable Syncfusion Flutter widgets.
platform: flutter
control: General
documentation: ug
---

# Globalization for Syncfusion widgets

## Date and number formats

Syncfusion Flutter widgets support formatting dates and numbers based on culture. For more details, you can refer to the following links.

<table>
    <tr>
        <td>
            <b>Widgets</b>
        </td>
        <td>
             <b>Reference Links</b>
        </td>
    </tr>
    <tr>
        <td>
            SfCartesianChart
        </td>
        <td>
             <a href="https://help.syncfusion.com/flutter/cartesian-charts/axis-types#numeric-axis">Number</a> <br/>
             <a href="https://help.syncfusion.com/flutter/cartesian-charts/axis-types#date-time-axis">Date</a>
        </td>
    </tr>
	<tr>
        <td>
            SfCalendar
        </td>
        <td>
            <a href="https://help.syncfusion.com/flutter/calendar/month-view#view-header-dayformat">Date</a>
        </td>
    </tr>
    <tr>
        <td>
            SfDateRangePicker
        </td>
        <td>
            <a href="https://help.syncfusion.com/flutter/daterangepicker/headers#view-header-day-format">Date</a>
        </td>
    </tr>
    <tr>
        <td>
           SfRangeSlider
        </td>
       <td>
           <a href="https://help.syncfusion.com/flutter/range-slider/labels-and-divisor#number-format">Number</a><br/>
           <a href="https://help.syncfusion.com/flutter/range-slider/labels-and-divisor#date-format">Date</a>
      </td>
  </tr>
  <tr>
        <td>
            SfRangeSelector
        </td>
        <td>
            <a href="https://help.syncfusion.com/flutter/range-selector/labels-and-divisor#number-format">Number</a><br/>
            <a href="https://help.syncfusion.com/flutter/range-selector/labels-and-divisor#date-format">Date</a>
        </td>
    </tr>
</table>

## Localizations

By default, the Syncfusion widgets are implemented with English localization (en-US) alone. You can add support for other languages by including our another package named [`syncfusion_localizations`](https://pub.dev/packages/syncfusion_localizations). As of now, this package supports 74 languages which are listed below.

*  af - Afrikaans 
*  am - Amharic 
*  ar - Arabic 
*  az - Azerbaijani 
*  be - Belarusian 
*  bg - Bulgarian 
*  bn - Bengali Bangla 
*  bs - Bosnian 
*  ca - Catalan Valencian 
*  cs - Czech 
*  da - Danish 
*  de - German 
*  el - Modern Greek 
*  en - English 
*  es - Spanish Castilian 
*  et - Estonian 
*  eu - Basque 
*  fa - Persian 
*  fi - Finnish 
*  fil - Filipino Pilipino 
*  fr - French 
*  gl - Galician 
*  gu - Gujarati 
*  he - Hebrew 
*  hi - Hindi 
*  hr - Croatian 
*  hu - Hungarian 
*  hy - Armenian 
*  id - Indonesian 
*  is - Icelandic 
*  it - Italian 
*  ja - Japanese 
*  ka - Georgian 
*  kk - Kazakh 
*  km - Khmer Central Khmer 
*  kn - Kannada 
*  ko - Korean 
*  ky - Kirghiz Kyrgyz 
*  lo - Lao 
*  lt - Lithuanian
*  lv - Latvian 
*  mk - Macedonian 
*  ml - Malayalam 
*  mn - Mongolian 
*  mr - Marathi 
*  ms - Malay 
*  my - Burmese 
*  nb - Norwegian Bokmål 
*  ne - Nepali 
*  nl - Dutch Flemish 
*  pa - Panjabi Punjabi 
*  pl - Polish 
*  ps - Pushto Pashto 
*  pt - Portuguese (+ one country variation) 
*  ro - Romanian Moldavian Moldovan 
*  ru - Russian 
*  si - Sinhala Sinhalese 
*  sk - Slovak 
*  sl - Slovenian 
*  sq - Albanian 
*  sr - Serbian 
*  sv - Swedish 
*  sw - Swahili 
*  ta - Tamil 
*  te - Telugu 
*  th - Thai 
*  tl - Tagalog 
*  tr - Turkish 
*  uk - Ukrainian 
*  ur - Urdu 
*  uz - Uzbek 
*  vi - Vietnamese 
*  zh - Chinese (+ 2 country variations) 
*  zu - Zulu


### How to localize the Syncfusion Flutter widgets?

Here, lets see how to localize texts in the calendar using our [`syncfusion_localizations`](https://pub.dev/packages/syncfusion_localizations) package.

To accomplish this add to your pub spec file the [`syncfusion_localizations`](https://pub.dev/packages/syncfusion_localizations) and the [`syncfusion_flutter_calendar`](https://pub.dev/packages/syncfusion_flutter_calendar) packages as dependency.

{% highlight dart %} 

    dependencies:
    syncfusion_flutter_calendar: ^xx.x.xx
    syncfusion_localizations: ^xx.x.xx

{% endhighlight %}

>**Note**: Here **xx.x.xx** denotes the current version of [`Syncfusion Flutter`](https://pub.dev/publishers/syncfusion.com/packages ) widgets.

To use the [`Syncfusion Localization`](https://pub.dev/packages/syncfusion_localizations) and [`Syncfusion Flutter Calendar`](https://pub.dev/packages/syncfusion_flutter_calendar) widgets, import the following libraries in your Dart code.

{% highlight dart %} 

    import 'package:syncfusion_flutter_calendar/calendar.dart';
    import 'package:syncfusion_localizations/syncfusion_localizations.dart';

{% endhighlight %}

After importing the required packages, initialize the [`calendar`](https://pub.dev/packages/syncfusion_flutter_calendar) widget as a child of any widget and specify [`localizationsDelegates`](https://api.flutter.dev/flutter/material/MaterialApp/localizationsDelegates.html) and [`supportedLocales`](https://api.flutter.dev/flutter/material/MaterialApp/supportedLocales.html) for the MaterialApp.

{% highlight dart %} 

    // Localizations configurations
    @override
    Widget build(BuildContext context) {
        return MaterialApp(
            localizationsDelegates: [
                // ... app-specific localization delegate[s] here
                SfGlobalLocalizations.delegate
            ],
            supportedLocales: [
                const Locale('en'),
                const Locale('fr'),
                // ... other locales the app supports
            ],
            locale: const Locale('fr'),
            home: MyHomePage(),
        );
    }

    // Calendar configurations
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            body: SfCalendar(
                view: CalendarView.month,
                // Other configurations
            )
        );
    }

{% endhighlight %}

The example for reference can be found [`here`](https://pub.dev/packages/syncfusion_localizations#-example-tab-).

And some languages may require more than language code to differentiate properly. Consider the Chinese language for example, here we can specify the language code, script code, and country code. This is because of the existence of simplified and traditional script, as well as regional differences in the way characters are written within the same script type.

{% highlight dart %} 

    supportedLocales: [
        // generic Chinese 'zh'
        const Locale.fromSubtags(languageCode: 'zh'), 

        // generic traditional Chinese 'zh_Hant'
        const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hant'), 

        // 'zh_Hant_TW'
        const Locale.fromSubtags(languageCode: 'zh', scriptCode: 'Hant', countryCode: 'TW'), 
    ],

{% endhighlight %}

![Chinese culture](globalization-images/localization_zh.png)

### Custom culture support

If you wish to add your own custom culture apart from the supported 74 languages, you can extend the [`SfLocalizations`](https://pub.dev/documentation/syncfusion_flutter_core/latest/localizations/SfLocalizations-class.html) class and override the required properties. This has been depicted in the following example for the Estonian(et) language.

**Step 1**

Create a dart file in your application and import the required packages.

{% highlight dart %} 

    import 'package:flutter/foundation.dart';
    import 'package:flutter/material.dart';
    import 'package:syncfusion_flutter_core/localizations.dart';
    
{% endhighlight %}

**Step 2**

 Create a class for `Estonian` which extends from [`SfLocalizations`](https://pub.dev/documentation/syncfusion_flutter_core/latest/localizations/SfLocalizations-class.html)

 {% highlight dart %} 

    /// The translations for Estonian (`et`).
    class SfLocalizationsEt extends SfLocalizations{
        SfLocalizationsEt();

        @override
        String get noEventsCalendarLabel => 'Pole valitud kuupäeva';

        @override
        String get noSelectedDateCalendarLabel => 'Üritusi pole';

        // other properties
    }

{% endhighlight %}

**Step 3**

Create a delegate for the `Estonian` language.

{% highlight dart %} 

    class SfLocalizationsEtDelegate extends LocalizationsDelegate<SfLocalizations> {
        const SfLocalizationsEtDelegate();

        @override
        bool isSupported(Locale locale) => locale.languageCode == 'et';

        @override
        Future<SfLocalizations> load(Locale locale) {
            return SynchronousFuture<SfLocalizations>(SfLocalizationsEt());
        }

        @override
        bool shouldReload(LocalizationsDelegate<SfLocalizations> old) => false;
    }

{% endhighlight %}


**Step 4**

Import the created dart file in your application and specify the [`localizationsDelegates`](https://api.flutter.dev/flutter/material/MaterialApp/localizationsDelegates.html), [`supportedLocales`](https://api.flutter.dev/flutter/material/MaterialApp/supportedLocales.html) and [`locale`](https://api.flutter.dev/flutter/package-intl_locale/package-intl_locale-library.html). Then run your application.

{% highlight dart %} 

    //import your dart file here
    import './localization_extendability.dart';

    @override
    Widget build(BuildContext context) {
        return MaterialApp(

            localizationsDelegates: [
                GlobalMaterialLocalizations.delegate,
                SfGlobalLocalizations.delegate,
                
                //Specify the delegate directly
                SfLocalizationsEtDelegate()
            ],

            supportedLocales: [
                const Locale('en'),

                //Specify the suported locales here
                const Locale('et'),
            ],

            //Specify the locale here
            locale: const Locale('et'),

            // Other configurations
        );
    }

{% endhighlight %}

![Localization](globalization-images/localization_extendability.png)

The sample for reference can be found below.

[`Custom Localization Sample`](https://www.syncfusion.com/downloads/support/directtrac/general/ze/sync_localizations275997229)