# Light of Islam Mosque Display

A full-screen prayer and community information display for the Light of Islam
Association in Brampton, Ontario. The page presents the monthly iqama schedule,
announcements, and donation information in a layout intended for a mosque
display screen.

## How it works

The display is a self-contained web page. Its 1920 × 1080 layout scales to fit
the browser window while keeping its proportions. The left panel shows the
association logo, a live clock with the current time and date, and supporting
information; the main area shows the title, prayer schedule, announcements,
and donation details.

The clock uses the display device's local time in 12-hour format with an AM/PM
indicator. It shows the weekday and calendar date beneath the time and updates
as the minutes change.

The schedule and supporting text come from CSV published from a Google Sheet.
Each row is identified by its `type`:

| Row type | Data |
| --- | --- |
| `setting` | A setting name and its value, such as the title, website, or donation information |
| `period` | A date range followed by the Fajr, Zuhr, Asr, Maghrib, and Isha iqama times |
| `announcement` | One announcement |

The display recognizes the settings `title`, `subtitle`, `note`, `website`,
`donation_text`, and `donation_email`. If no subtitle is supplied, it shows the
current Gregorian and Hijri month and year based on the display device's date.
Schedule ranges using an English month and day range, such as `Oct 1-10`, are
highlighted when they include the device's current local date.

When the page opens, it renders the most recently cached sheet data if
available; otherwise it starts with the sample schedule embedded in the page.
It then requests the published CSV and checks for updates every five minutes.
Successfully loaded data replaces the current display and is saved in the
browser's local storage for the next page load. The display also refreshes its
date-range highlighting once a minute.

Clicking the page or pressing **F** requests browser full-screen mode.
