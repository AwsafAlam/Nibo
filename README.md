Nibo library for Android
====================================

Android library that provides UI for a customizable place picker, origin and destination picker and Google Places autocomplete searchview

Current stable version - 0.10
---------------

**This version uses Google Play Services 11.0.4 and RxJava 2.0.+**

What can you do with this?
--------------------------
* Easily add a Google Places autocomplete searchview widget to your project
* Pick a location from a map
 - Can be customized to match the theme of your app
 - Can use customized map markers
 - Can drag map marker to select location
 - Can search for location names
 - uses a fragment which you can overide and add extra functionality
* Pick a origin location and a destination location (like Uber)
 - Can be customized to match the theme of your app
 - Can use custom map markers for each location

What does the UI look like?
----------------------------
|       ROW 1  |        ROW 2    |   
| ------------- |:-------------:|
| <img src="GIFS/searchviewgif.gif" width="350"/>    | <img src="GIFS/locationpikcer.gif" width="350"/> |
| <img src="GIFS/originsourcepickerdefault.gif" width="350"/> | <img src="GIFS/originsourcepickerbluestyled.gif" width="350"/> |


How do I use this?
----------------------------
#### Using NiboPlaceAutoCompleteSearchView
Simple. All you need is to do is:
- Add the following to your layout (You can change the values as you wish)

```xml
<com.alium.nibo.autocompletesearchbar.NiboPlacesAutoCompleteSearchView
        android:id="@+id/autocompletesearchbar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:elevation="4dp"
        app:niboSV_customToolbarHeight="?attr/actionBarSize"
        app:niboSV_displayMode="toolbar"
        app:niboSV_editHintText="Search"
        app:niboSV_editHintTextColor="#757575"
        app:niboSV_editTextColor="#757575"
        app:niboSV_homeButtonMode="burger"
        app:niboSV_searchCardElevation="2dp"
        app:niboSV_searchTextColor="#757575" />
```
- In your fragment or activity, implement NiboAutocompleteSVProvider, and return a valid GoogleAPIClient object and an instance of NiboPlacesAutoCompleteSearchView.SearchListener (see example app for better explanation)

- Call setmProvider(this) on your seachview.


#### Using NiboOriginDestinationPickerUI
- Add the following to your manifest file. NiboOrigDestTheme.NoActionBar gives you the default (white and black) styling.

```xml
<activity
           android:name="com.alium.nibo.origindestinationpicker.NiboOriginDestinationPickerActivity"
           android:label="@string/title_activity_origin_destination_picker"
           android:theme="@style/NiboOrigDestTheme.NoActionBar" />

```

- To use a custom style, see *NiboActivityStyle* style in the niboexample project. Make sure your theme has NiboOrigDestTheme.NoActionBar as a parent.

- To start the activity:

```java
Intent intent = new Intent(this, NiboOriginDestinationPickerActivity.class);

        NiboOriginDestinationPickerActivity.NiboOriginDestinationPickerBuilder config = new NiboOriginDestinationPickerActivity.NiboOriginDestinationPickerBuilder()
                .setDestinationMarkerPinIconRes(R.drawable.ic_map_marker_black_36dp)
                .setOriginMarkerPinIconRes(R.drawable.ic_map_marker_black_36dp)
                .setOriginEditTextHint("Input pick up location")
                .setPrimaryPolyLineColor(R.color.colorPrimary)
                .setSecondaryPolyLineColor(R.color.colorAccent)
                .setDestinationEditTextHint("Input destination")
                .setStyleEnum(NiboStyle.SUBTLE_GREY_SCALE);

        NiboOriginDestinationPickerActivity.setBuilder(config);
        startActivityForResult(intent, REQUEST_CODE);
```

- You can customize it other things like the directions Polyline color using the NiboOriginDestinationPickerBuilder as shown above.


#### Using NiboPlacePickerUI
- To start the activity:

```java
Intent intent = new Intent(this, NiboPlacePickerActivity.class);
 NiboPlacePickerActivity.NiboPlacePickerBuilder config = new NiboPlacePickerActivity.NiboPlacePickerBuilder()
         .setSearchBarTitle("Search for an area")
         .setConfirmButtonTitle("Pick here bish")
         .setMarkerPinIconRes(R.drawable.ic_map_marker_black_36dp)
         .setStyleEnum(NiboStyle.NIGHT_MODE);
         .setStyleFileID(R.raw.retro);
 NiboPlacePickerActivity.setBuilder(config);
 startActivityForResult(intent, REQUEST_CODE);
```
- You can customize it other things like the directions Polyline color using the NiboPlacePickerBuilder as shown above.



How to add to your project?
--------------
### Gradle


### Manual

Sample
------
Sample usage is available in *niboexample* directory.

Places API requires API Key. Before running samples you need to create project on API console
and obtain API Key from [here](https://developers.google.com/places/android/signup).
Obtained key should used to replace string named: ```google_places_key``` in ```google_maps_api.xml``` file.


References
------

If you need the SearchView without all the Google Places stuff, look at [PersistentSearchView ](https://github.com/crysehillmes/PersistentSearchView).

License
=======

    Copyright (C) 2017 Aliu Abdul-Mujeeb (http://www.oct-labs.com/mujib)

	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at

	     http://www.apache.org/licenses/LICENSE-2.0

	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.
