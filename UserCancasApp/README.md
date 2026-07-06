# User Canvas App

A responsive Microsoft Power Apps Canvas Application built as part of my PL-200 learning journey.

This application demonstrates how to build a complete CRUD experience using Dataverse, Forms, Galleries, Navigation, Relationships, Variables, Components, Collections, and Power Fx.

---

# Project Overview

The application manages Microsoft Dataverse Users and their assigned Devices.

The project started with a simple User Gallery, then gradually evolved into a complete multi-screen business application.

---

# Technologies Used

- Microsoft Power Apps (Canvas App)
- Microsoft Dataverse
- Power Fx
- Components
- Collections
- Variables
- Forms
- Galleries

---

# Features

## User Management

- Display Users from Dataverse
- Responsive Gallery
- Display User Details
- Edit User Information
- Submit Changes
- Cancel Changes
- Refresh User List

---

## Device Management

Created a custom **Device** table including:

- Device ID (Primary Name)
- Device Name
- Device Type
- Serial Number
- Device Status
- Purchase Date
- Original Purchase Value
- Current Value
- Device Image

---

## Dataverse Relationships

Implemented a One-to-Many relationship:

```
One User
      │
      └────────── Multiple Devices
```

Each User can own multiple Devices.

Each Device belongs to only one User.

---

## Calculated & Rollup Columns

### Calculated Column

Implemented a calculated field:

```
Depreciation

Original Purchase Value
        -
Current Value
```

### Rollup Column

Implemented a Rollup column on the User table that automatically calculates:

```
Total Original Purchase Value
```

for all devices owned by the selected User.

---

## Navigation

Implemented multi-screen navigation using:

- Navigate()
- Back()

The application contains:

- User Gallery
- User Details
- User Edit
- Device Gallery
- Device Edit
- Component Screen

---

## Forms

Used

- Display Form
- Edit Form

Implemented:

- SubmitForm()
- ResetForm()

for saving and cancelling edits.

---

## Device Filtering

Implemented Device filtering based on the selected User.

```PowerFx
Filter(
    Devices,
    User.User = UserGallery.Selected.User
)
```

Only devices assigned to the selected User are displayed.

---

## Images

Implemented image upload using the Add Picture control and linked it to the Dataverse Image column.

---

## Global Variables

Used Set() to switch between:

- Devices owned by the selected User
- All Devices

---

## Context Variables

Implemented sorting using Context Variables.

The gallery dynamically switches between:

- Ascending
- Descending

sorting.

---

## Search

Implemented live searching using:

```PowerFx
Search()
```

allowing users to quickly locate records.

---

## Components

Created a reusable Date Component.

The component exposes two output properties:

- DatePlus7
- DatePlus28

using:

```PowerFx
DateAdd(
    SelectedDate,
    7,
    TimeUnit.Days
)
```

and

```PowerFx
DateAdd(
    SelectedDate,
    28,
    TimeUnit.Days
)
```

The component can be reused across different screens.

---

## Collections

Built a separate Meeting Tracker application demonstrating Collections.

Features include:

- Date Picker
- Time
- Location
- Meeting With

Implemented:

- Collect()
- Clear()
- SaveData()
- LoadData()

Data is stored locally inside a Collection and displayed using a Data Table.

---

# Power Fx Functions Used

- Filter()
- Search()
- SortByColumns()
- If()
- Set()
- UpdateContext()
- Navigate()
- Back()
- SubmitForm()
- ResetForm()
- Refresh()
- Collect()
- ClearCollect()
- SaveData()
- LoadData()
- DateAdd()

---

# What I Learned

Throughout this project I learned how to:

- Build responsive Canvas Apps
- Design multi-screen navigation
- Connect Canvas Apps with Dataverse
- Create Dataverse relationships
- Work with Calculated and Rollup columns
- Build reusable Components
- Use Collections for temporary local storage
- Apply Power Fx functions effectively
- Improve application usability with Search, Sorting, Images, and Variables

---

# Screenshots



---

# Author

**Asmaa Salah Ibrahim**

Microsoft Power Platform (PL-200) Learning Journey
