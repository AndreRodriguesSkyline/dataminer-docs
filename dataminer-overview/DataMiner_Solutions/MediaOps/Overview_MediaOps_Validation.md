---
uid: Overview_MediaOps_Validation
---

# Validation

## Validation of upcoming bookings

To ensure smooth operations, it's essential that each booking is properly configured and that all required resources are available when the booking starts. To achieve this, a scheduled task runs every hour to validate the upcoming bookings set to start within the next hour.

When an error is detected, an error flag is activated in the booking object to make it visible that something is not correct with a red color.

![Job with error(s)](~/dataminer-overview/images/MediaOps_validation_error_job.png)

A detailed list of identified issues is accessible by opening the booking and clicking the error icon.

![Job error icon](~/dataminer-overview/images/MediaOps_validation_error_icon.png)

This opens a popup that contains a table listing all detected errors.

![Job error list](~/dataminer-overview/images/MediaOps_validation_error_list.png)

Detected errors cannot be cleared individually by a user. Instead, any change to the booking will automatically trigger a re-validation of the entire object. Errors that are no longer detected are automatically removed from the list.

### Customization of the interval and period

By default, the scheduled task triggers validation every hour. You can adjust this schedule by editing the **MediaOps // Scheduling - Validate upcoming bookings** scheduled task. This task will not be touched anymore when installing an upgrade package, as long as the name hasn't changed.

- **Interval**: Modify the "repeat every" setting on the Schedule tab to set how often the task runs. Default value: 60 minutes.
- **Validation Period**: Modify the period for upcoming bookings (e.g., next x minutes) on the Actions tab. The "Scheduling_Validate Upcoming" script has a parameter that specifies the validation period in minutes. Default value: 60 minutes.

These settings allow to adapt the validation timings according to your specific needs.

### Current tests

The following tests are being executed on job instances:

- All resources exist and are valid
- All mandatory configuration is done
- All virtual signal groups exist and are valid (if defined on resource)
- All flows exist and are valid (if VSG defined on resource)

This is currently still very basic, but can easily be extended in the future.

## Implementation of tests

A flexible and extendable framework has been designed to validate various types of objects within MediaOps. This framework is capable of validating multiple object types such as jobs, resources, resource pools, and others. The result of these tests are stored in the DOM object in a standardized and generic way. Adding new validation checks or modifying existing ones can be done with minimal effort.
