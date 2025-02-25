[![vanilla-calendar preview](https://vanilla-calendar.frontend.uvarov.tech/preview.png)](https://vanilla-calendar.frontend.uvarov.tech/)
# Vanilla JS Calendar v1.4.8

A simple yet feature rich calendar with no dependencies and no «input» tag. A lightweight date picker written in pure JavaScript.
The size of the minified file .js is approximately **22kb** and **5.3kb** gzip.

[DEMO](https://vanilla-calendar.frontend.uvarov.tech/)

This plugin is completely free, any support from you is important, please report problems or new ideas, it's really important!

If you like the plugin, consider ...

[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

## Implementation

Since Vanilla Calendar is written in pure JavaScript, it can be used with any modern framework or library, be it Vue,
React or Angular. You can get the plugin
by [downloading](https://vanilla-calendar.frontend.uvarov.tech/vanilla-calendar-v1.4.8.zip) it manually,
via [cdn](https://cdn.jsdelivr.net/npm/@uvarov.frontend/vanilla-calendar@1.4.8/) or via a package manager like npm:

```sh
npm install @uvarov.frontend/vanilla-calendar
```

Then import it in your javascript file.

```js
import VanillaCalendar from '@uvarov.frontend/vanilla-calendar';
```

And don't forget to import the base plugin styles in your stylesheet:

```css
@import '@uvarov.frontend/vanilla-calendar/vanilla-calendar.min.css';
```

If you have downloaded the plugin or are using it via cdn, you need to embed the plugin in your page, you should include
all required files in the **head** tag of your HTML document:

```html

<html>
<head>
  <!-- Plugin CSS -->
  <link href="./vanilla-calendar.min.css" rel="stylesheet">
  <!-- Plugin JS -->
  <script src="./vanilla-calendar.min.js" defer></script>
</head>
<body>
</body>
</html>
```

## Documentation

The first argument can be either an HTML element selector or the element itself. The second optional argument can be passed options that define the calendar settings.

```js
new VanillaCalendar(selector || object[, options]);
```

### Main parameters

| Name                         |    Type     |   Default    | Description                                                                                                                                                      |
|------------------------------|:-----------:|:------------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| type                         |   String    |  'default'   | Calendar type. Possible options: 'default', 'month', 'year'.                                                                                                     |
| date.min                     |   String    | '1970-01-01' | The minimum possible date that the calendar will take into account.                                                                                              |
| date.max                     |   String    | '2470-12-31' | The maximum possible date that the calendar will take into account.                                                                                              |
| date.today                   | Date object |  new Date()  | Specifies which day the calendar will consider today.                                                                                                            |

### Settings

| Name                               |  Type   | Default  | Description                                                                                                                                       |
|------------------------------------|:-------:|:--------:|---------------------------------------------------------------------------------------------------------------------------------------------------|
| settings.lang                      | String  |   'en'   | Indicates what language the labels will be in. Specify a BCP 47 locale or 'define' to assign your own month and week names, see demo for details. |
| settings.iso8601                   | Boolean |   true   | Weeks in ISO 8601 format.                                                                                                                         |
| settings.range.min                 | String  |   null   | Dates less than this will be considered disabled.                                                                                                 |
| settings.range.max                 | String  |   null   | Dates greater than this will be considered disabled.                                                                                              |
| settings.range.disabled            |  Array  |   null   | Force the specified dates to be disabled.                                                                                                         |
| settings.selection.day             | String  | 'single' | Allow to choose a days. Possible options: 'single', 'multiple', 'multiple-ranged'.                                                                |
| settings.selection.month           | Boolean |   true   | Allow to select a month.                                                                                                                          |
| settings.selection.year            | Boolean |   true   | Allow to select a year.                                                                                                                           |
| settings.selected.dates            |  Array  |   null   | List of days to be selected.                                                                                                                      |
| settings.selected.month            | Number  |   null   | Selected month by default.                                                                                                                        |
| settings.selected.year             | Number  |   null   | Selected year by default.                                                                                                                         |
| settings.selected.holidays         |  Array  |   null   | The specified days will be considered additional days off.                                                                                        |
| settings.visibility.templateHeader | String  | '%M %Y'  | Customize the title of the calendar. %M - month display pattern, %Y - year display pattern.                                                       |
| settings.visibility.monthShort     | Boolean |   true   | Abbreviate month names in the month selection.                                                                                                    |
| settings.visibility.weekNumbers    | Boolean |  false   | Show week numbers.                                                                                                                                |
| settings.visibility.weekend        | Boolean |   true   | Highlight the weekend.                                                                                                                            |
| settings.visibility.today          | Boolean |   true   | Highlight the today.                                                                                                                              |
| settings.visibility.disabled       | Boolean |  false   | Show disabled days.                                                                                                                               |

### Locale

| Name           | Type  | Default | Description                                                                                      |
|----------------|:-----:|:-------:|--------------------------------------------------------------------------------------------------|
| locale.months  | Array |  null   | 	An array with custom month names. Only works when "settings.lang" is set to "define".           |
| locale.weekday | Array |  null   | An array with custom abbreviated week names. Only works when "settings.lang" is set to "define". |

### Methods

| Name                         |    Type     |   Default    | Description                                                                                                                                                      |
|------------------------------|:-----------:|:------------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| actions.clickDay             |  Function   |     null     | The method is triggered after clicking on a day in the calendar, but before other operations.                                                                    |
| actions.clickMonth           |  Function   |     null     | The method is triggered after clicking on a month in the calendar, but before other operations.                                                                  |
| actions.clickYear            |  Function   |     null     | The method is triggered after clicking on a year in the calendar, but before other operations.                                                                   |

### Popups

| Name                  |  Type  | Default | Description                                                                                                                                           |
|-----------------------|:------:|:-------:|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| popups[date]          | String |  null   | The «popups» object accepts a date as an object key, such as «popups['2022-06-29']». Note the required date format 'YYYY-MM-DD'.                      |
| popups[date].modifier | String |  null   | The «popups[date].modifier» object takes a modifier class as its value. This class allows you to highlight the date using styles.                     |
| popups[date].html     | String |  null   | 	The «popups[date].html» object takes as its value a string that is rendered to HTML. You can pass plain text or full HTML markup to style the popup. |

## Usage example

```js
const calendar = new VanillaCalendar('.vanilla-calendar', {
  type: 'month',
  date: {
    min: '2000-01-01',
    max: '2030-12-31',
    today: new Date('2022-01-07'),
  },
  settings: {
    lang: 'define',
    iso8601: true,
    range: {
      min: '2022-01-01',
      max: '2022-02-12',
      disabled: ['2022-01-25'],
    },
    selection: {
      day: 'multiple',
      month: false,
      year: false,
    },
    selected: {
      dates: ['2022-01-09', '2022-01-10'],
      month: 1,
      year: 2022,
      holidays: ['2022-01-02', '2022-01-03', '2022-01-04', '2022-01-05'],
    },
    visibility: {
      templateHeader: '> %M | %Y <',
      monthShort: false,
      weekNumbers: true,
      weekend: false,
      today: true,
      disabled: true,
    },
  },
  locale: {
    months: ['Қаңтар', 'Ақпан', 'Наурыз', 'Сәуір', 'Мамыр', 'Маусым', 'Шілде', 'Тамыз', 'Қыркүйек', 'Қазан', 'Қараша', 'Желтоқсан'],
    weekday: ['Си', 'Же', 'Ду', 'Сй', 'Ср', 'Бе', 'Жұ'],
    // Example:
    // months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
    // weekday: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
    // Note that the weeks array must start with Sunday, this does not affect ISO 8601.
  },
  actions: {
    clickDay(e) {
      alert(e.target.dataset.calendarDay);
    },
    clickMonth(e) {
      alert(e.target.dataset.calendarMonth);
    },
    clickYear(e) {
      alert(e.target.dataset.calendarYear);
    },
  },
  popups: {
    '2022-06-28': {
      modifier: 'bg-red',
      html: 'Meeting at 9:00 PM',
    },
    '2022-07-13': {
      modifier: 'bg-red',
      html: 'Meeting at 6:00 PM',
    },
    '2022-07-17': {
      modifier: 'bg-orange',
      html: `<div>
        <u><b>12:00 PM</b></u>
        <p style="margin: 5px 0 0;">Airplane in Las Vegas</p>
      </div>`,
    },
  },
});

calendar.init();
```

Change settings and update:

```js
calendar.date.today = new Date('2022-01-25');
calendar.settings.lang = 'en';
calendar.settings.iso8601 = false;
calendar.settings.selected.date = '2022-01-15';

calendar.update();
```

## License

MIT License

## Author

Yuri Uvarov (*uvarov.frontend@gmail.com*)

[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg
[buymeacoffee]: https://www.buymeacoffee.com/uvarov
