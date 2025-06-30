##

---

### Modus Classic Themes: Prototyping Guide for Gemini Canvas

This guide provides the necessary resources to quickly create HTML prototypes using the Modus Classic Light and Classic Dark themes.

### HTML Page Setup for Prototypes

This is the minimal boilerplate for an HTML page using Modus Styles.

#### 1. Add Links to `<head>`

Place the following links in the `<head>` of your HTML document.

```html
<!-- Important! Modus component tokens & styles -->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-web-components@latest/dist/modus-wc-styles.css"
/>

<!-- Google Fonts: Open Sans (Required by Modus) -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap"
  rel="stylesheet"
/>

<!-- Important! Modus Icons -->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/field-systems/fonts/modus-icons.css"
/>

<!-- (Optional) Tailwind CSS for utility classes -->
<script src="https://cdn.tailwindcss.com"></script>
```

#### 2. Set the Default Theme

The root `<html>` tag must have a `data-theme` attribute. `modus-classic-light` is the default.

```html
<html lang="en" data-theme="modus-classic-light">
  <!-- Your content here -->
</html>
```

Available themes in this guide: `modus-classic-light` and `modus-classic-dark`.

#### 3. (Optional) Add a Theme Switcher

For quick prototyping, you can add this simple dropdown to your page to switch between themes.

```html
<select
  class="modus-wc-select modus-wc-select-bordered"
  onchange="document.documentElement.setAttribute('data-theme', this.value)"
>
  <option value="modus-classic-light">Classic Light</option>
  <option value="modus-classic-dark">Classic Dark</option>
</select>
```

**Pro-tip:** To persist the user's choice, you can save the value to `localStorage` and re-apply it when the page loads.

#### 4. (Optional) Additional Libraries

For data visualization prototypes, you can include libraries like Chart.js.

```html
<!-- Chart.js for data visualization -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
```

### 5. Using Modus Icons (Icon Font Method)

To use an icon, add an `<i>` tag with the class `modus-icons`. The name of the icon (from the list below) should be placed as text between the opening and closing tags.

##### **Basic Usage**

```html
<!-- Renders a lightbulb icon -->
<i class="modus-icons">lightbulb_on</i>

<!-- Renders a settings icon -->
<i class="modus-icons">settings</i>
```

##### **Customizing Size and Color**

Since these are font icons, you can change their appearance using standard `font-size` and `color` CSS properties.

```html
<!-- A larger, orange lightbulb icon -->
<i class="modus-icons" style="font-size: 2rem; color: orange;">lightbulb_on</i>

<!-- A button with a customized icon -->
<button class="modus-wc-btn">
  <i class="modus-icons" style="font-size: 1.5rem;">add</i>
  <span>Add Item</span>
</button>
```

#### Available Icon Names

|                                      |                                         |                                  |
| ------------------------------------ | --------------------------------------- | -------------------------------- |
| `2_layers`                           | `2_layers_off`                          | `360`                            |
| `3d_buildings`                       | `accessibility`                         | `accessibility_circle`           |
| `account_circle`                     | `add`                                   | `add_bold`                       |
| `add_circle`                         | `add_heavy`                             | `add_new_road`                   |
| `add_square`                         | `address`                               | `advanced_instructions`          |
| `alarm_add`                          | `alarm_off`                             | `alarm_on`                       |
| `alert`                              | `alert_outlined`                        | `align_bottom`                   |
| `align_center_horiz`                 | `align_center_vert`                     | `align_left`                     |
| `align_right`                        | `align_top`                             | `angle_90`                       |
| `antenna`                            | `apps`                                  | `arc`                            |
| `archive_square`                     | `arrow_back`                            | `arrow_down`                     |
| `arrow_down_circle`                  | `arrow_expand_diagonal_left`            | `arrow_expand_diagonal_right`    |
| `arrow_left`                         | `arrow_left_circle`                     | `arrow_next`                     |
| `arrow_right`                        | `arrow_right_circle`                    | `arrow_up`                       |
| `arrow_up_circle`                    | `artificial_intelligence`               | `auto_target`                    |
| `avoidance_zone`                     | `background_dark`                       | `background_light`               |
| `backup_restore_cloud`               | `backup_restore_file`                   | `bar_graph`                      |
| `bar_graph_line`                     | `bar_graph_square`                      | `barcode`                        |
| `base_station`                       | `battery_0_horizontal`                  | `battery_0_vertical`             |
| `battery_25_horizontal`              | `battery_25_vertical`                   | `battery_50_horizontal`          |
| `battery_50_vertical`                | `battery_75_horizontal`                 | `battery_75_vertical`            |
| `battery_charging_horizontal`        | `battery_charging_vertical`             | `battery_full_horizontal`        |
| `battery_full_vertical`              | `between`                               | `blank`                          |
| `blocks_four`                        | `blocks_four_outline`                   | `bolt`                           |
| `bookings`                           | `bookings_open`                         | `box_select`                     |
| `box_zoom`                           | `briefcase`                             | `brightness`                     |
| `brush`                              | `bug`                                   | `bug_report`                     |
| `building_corporate`                 | `buildings`                             | `bullseye`                       |
| `bullseye_off`                       | `bullseye_warning`                      | `calculate`                      |
| `calculator`                         | `calculator_symbols`                    | `calendar`                       |
| `calendar_add`                       | `calendar_and_key`                      | `calendar_blank`                 |
| `calendar_booking`                   | `calendar_cancel`                       | `calendar_check`                 |
| `calendar_clock`                     | `calendar_event`                        | `calendar_loading_unloading`     |
| `calendar_loading_unloading_date`    | `calendar_plus`                         | `calendar_rebook`                |
| `calendar_reserve`                   | `calendar_show`                         | `calendar_time_slot`             |
| `calendar_week`                      | `camera`                                | `camera_disabled`                |
| `camera_photo_add`                   | `cancel_circle`                         | `cancel_square`                  |
| `cancel_square_outlined`             | `car`                                   | `car_front`                      |
| `caret_down`                         | `caret_down_bold`                       | `caret_left`                     |
| `caret_left_bold`                    | `caret_right`                           | `caret_right_bold`               |
| `caret_up`                           | `caret_up_bold`                         | `cell_merge`                     |
| `cell_properties`                    | `cell_split`                            | `certificate`                    |
| `change_start_time`                  | `chat`                                  | `check`                          |
| `check_bold`                         | `check_circle`                          | `check_circle_outlined`          |
| `check_heavy`                        | `checkbox_checked`                      | `checkbox_unchecked`             |
| `chevron`                            | `chevron_double_down`                   | `chevron_double_left`            |
| `chevron_double_right`               | `chevron_double_up`                     | `chevron_left`                   |
| `chevron_left_bold`                  | `chevron_right`                         | `chevron_right_bold`             |
| `circle`                             | `circle_dot`                            | `circle_dot_outline`             |
| `circle_notch`                       | `circle_outline`                        | `circle_play`                    |
| `clip`                               | `clipboard`                             | `clipboard_actions`              |
| `clipboard_check`                    | `clipboard_empty`                       | `clipboard_planning`             |
| `clock`                              | `clock_add`                             | `clock_checkmark`                |
| `clock_delay_warning`                | `clock_delayed`                         | `clock_locked`                   |
| `clock_question_mark`                | `close`                                 | `close_bold`                     |
| `close_heavy`                        | `cloud`                                 | `cloud_connected`                |
| `cloud_disconnected`                 | `cloud_download`                        | `cloud_upload`                   |
| `cluster`                            | `code`                                  | `coffee_cup`                     |
| `collapse`                           | `collapse_bold`                         | `color_picker`                   |
| `column_copy`                        | `column_cut`                            | `column_delete`                  |
| `column_insert_after`                | `column_insert_before`                  | `column_paste_after`             |
| `column_paste_before`                | `column_properties`                     | `columns`                        |
| `combine`                            | `comment`                               | `comment_add`                    |
| `comment_empty`                      | `comment_message`                       | `comment_message_disabled`       |
| `company_administration`             | `compactor`                             | `compare_arrows`                 |
| `compass`                            | `component`                             | `configuration_management`       |
| `contacts`                           | `contrast`                              | `copy_content`                   |
| `corner`                             | `costs`                                 | `credit_card`                    |
| `crop`                               | `crow_fly`                              | `cube`                           |
| `curly_brackets`                     | `cursor`                                | `cursor_add`                     |
| `cursor_remove`                      | `dashboard`                             | `dashboard_tiles`                |
| `data_missing`                       | `data_transfer_off`                     | `day_mostly_cloudy`              |
| `day_partly_cloudy`                  | `delete`                                | `delivery_truck`                 |
| `delivery_truck_allocate`            | `delivery_truck_motion`                 | `design_package`                 |
| `device_cb460`                       | `device_tsc7`                           | `devices_group`                  |
| `devices_status`                     | `disk`                                  | `dispatch`                       |
| `document`                           | `download`                              | `download_line`                  |
| `download_xls`                       | `dozer`                                 | `drag_corner`                    |
| `drag_horizontal`                    | `drag_indicator`                        | `drag_vertical`                  |
| `driver`                             | `driver_groups`                         | `drivers`                        |
| `drizzle`                            | `drone`                                 | `earnings_statement`             |
| `easting`                            | `edit`                                  | `edit_combination`               |
| `edit_line`                          | `edit_mode`                             | `edit_road`                      |
| `electric_meter_off`                 | `electric_meter_off_outline`            | `electric_meter_outline_rounded` |
| `electric_meter_rounded`             | `electric_meter_rounded_warn`           | `elevation`                      |
| `email`                              | `email_add`                             | `envelope`                       |
| `eraser`                             | `exclamation_mark`                      | `expand`                         |
| `expand_bold`                        | `expand_less`                           | `expand_less_bold`               |
| `expand_less_circle`                 | `expand_more`                           | `expand_more_bold`               |
| `expand_more_circle`                 | `export`                                | `expression`                     |
| `external_link`                      | `eyedropper`                            | `factory`                        |
| `fast_forward`                       | `fast_rewind`                           | `file`                           |
| `file_bar_graph`                     | `file_check_in`                         | `file_check_out`                 |
| `file_cloud`                         | `file_copy`                             | `file_edit`                      |
| `file_merge`                         | `file_missing`                          | `file_new`                       |
| `file_secure`                        | `file_table`                            | `file_type_bmpf`                 |
| `file_type_csv`                      | `file_type_cur`                         | `file_type_doc`                  |
| `file_type_ico`                      | `file_type_key`                         | `file_type_log`                  |
| `file_type_numbers`                  | `file_type_pdf`                         | `file_type_pem`                  |
| `file_type_rfi`                      | `file_type_rfq`                         | `file_type_rtf`                  |
| `file_type_text`                     | `file_type_tif`                         | `file_type_tmp`                  |
| `file_type_xls`                      | `filter`                                | `filter_list`                    |
| `filter_off`                         | `finalize_route`                        | `first_page`                     |
| `flag`                               | `flag_finish`                           | `flash_on`                       |
| `floorplan`                          | `flowchart`                             | `fog`                            |
| `folder_closed`                      | `folder_locked`                         | `folder_new`                     |
| `folder_open`                        | `folder_personal`                       | `folder_project`                 |
| `folder_public`                      | `folder_share`                          | `folder_unlocked`                |
| `footprints`                         | `forestry`                              | `forklift`                       |
| `format_code`                        | `frame`                                 | `frame_stop`                     |
| `freight_market`                     | `freight_matching`                      | `freight_trolley`                |
| `full_screen`                        | `function`                              | `gantt_chart`                    |
| `gavel`                              | `gears`                                 | `geocode`                        |
| `globe`                              | `gnss`                                  | `gnss_r8`                        |
| `gnss_r8s_base`                      | `gnss_rpt`                              | `gnss_rts`                       |
| `gnss_sps986`                        | `gps`                                   | `grader`                         |
| `greater_than_equal_to`              | `group_items`                           | `hail`                           |
| `hail_heavy`                         | `hail_light`                            | `hammer`                         |
| `hand`                               | `hand_pan`                              | `hard_hat`                       |
| `headset`                            | `heart`                                 | `heavy_duty`                     |
| `helicopter`                         | `help`                                  | `help_outlined`                  |
| `hex`                                | `highway`                               | `history`                        |
| `home`                               | `horizontal_accuracy`                   | `hourglass`                      |
| `ice`                                | `icons_shapes`                          | `image`                          |
| `image_add`                          | `image_disabled`                        | `image_scene`                    |
| `image_square`                       | `image_square_off`                      | `image_square_off_outline`       |
| `image_square_outline`               | `in_cab_device`                         | `in_field_device`                |
| `info`                               | `info_outlined`                         | `info_token`                     |
| `inspect`                            | `invert_route`                          | `invoice`                        |
| `invoice_euro`                       | `invoice_pound`                         | `invoice_yen`                    |
| `item_begins_with`                   | `item_contains`                         | `item_does_not_contain`          |
| `item_does_not_equal`                | `item_ends_with`                        | `item_equals`                    |
| `key`                                | `keyboard`                              | `keyboard_keys`                  |
| `labs`                               | `language`                              | `last_page`                      |
| `launch`                             | `launch_bold`                           | `layer`                          |
| `layer_background`                   | `layer_circle`                          | `layer_circle_filled`            |
| `layer_fill`                         | `layer_heatmap`                         | `layer_line`                     |
| `layer_raster`                       | `layer_symbol`                          | `layout`                         |
| `learn`                              | `less_than_equal_to`                    | `light_duty`                     |
| `lightbulb_off`                      | `lightbulb_on`                          | `lightning`                      |
| `line_diagonal`                      | `line_graph`                            | `link`                           |
| `link_broken`                        | `link_off`                              | `list_bulleted`                  |
| `list_numbered`                      | `list_shapes`                           | `load`                           |
| `location`                           | `location_add`                          | `location_add_multiple`          |
| `location_arrow`                     | `location_disabled`                     | `location_point`                 |
| `lock`                               | `lock_open`                             | `machine`                        |
| `machines`                           | `magic_wand`                            | `manage_accounts`                |
| `manage_people`                      | `manage_places`                         | `manage_route_modifiers`         |
| `map`                                | `map_2d`                                | `map_layers`                     |
| `map_marker`                         | `map_marker_circle`                     | `map_marker_multiple`            |
| `map_markers`                        | `map_poi`                               | `master_data`                    |
| `maximize`                           | `measure_up`                            | `medium_duty`                    |
| `megaphone`                          | `menu`                                  | `menu_circle`                    |
| `mic`                                | `minimize`                              | `mix`                            |
| `mobile_app_version`                 | `monetarization`                        | `moon`                           |
| `more_circle`                        | `more_horizontal`                       | `more_vertical`                  |
| `mouse`                              | `move`                                  | `move_last_down`                 |
| `move_last_left`                     | `move_last_right`                       | `move_last_up`                   |
| `my_edits`                           | `my_places`                             | `my_trip`                        |
| `night_mostly_cloudy`                | `night_partly_cloudy`                   | `no_entry`                       |
| `no_package`                         | `no_truck`                              | `northing`                       |
| `not_synced_bold`                    | `notifications`                         | `notifications_off`              |
| `object_mirror`                      | `object_outline`                        | `object_rotate`                  |
| `offers`                             | `one_way_left`                          | `one_way_right`                  |
| `optimize`                           | `orbit`                                 | `orders`                         |
| `orthogonal`                         | `overcast`                              | `package`                        |
| `package_delivered`                  | `package_delivery`                      | `package_missing`                |
| `package_pickup`                     | `package_sent`                          | `pager`                          |
| `paint_bucket`                       | `palette`                               | `pan`                            |
| `paper_plane`                        | `paperclip`                             | `password`                       |
| `pause_circle`                       | `payment_instant`                       | `pen`                            |
| `pencil`                             | `people_add`                            | `people_couple`                  |
| `people_group`                       | `person`                                | `person_account`                 |
| `person_add`                         | `person_clock`                          | `person_edit`                    |
| `person_remove`                      | `perspective`                           | `phone`                          |
| `phone_call`                         | `phone_hang_up`                         | `phone_mobile`                   |
| `pin`                                | `pin_add`                               | `pin_icon`                       |
| `pin_icon_plus`                      | `pin_straight`                          | `pin_straight_cancel`            |
| `play_circle`                        | `point_marker_tool`                     | `poi`                            |
| `polygon`                            | `polygon_area_tool`                     | `polygon_concave`                |
| `polygon_cone`                       | `polygon_drag_rectangle`                | `polygon_line_tool`              |
| `polygon_merge`                      | `polygon_select`                        | `preview`                        |
| `printer`                            | `prism_pole`                            | `prism_pole_extend`              |
| `pulse`                              | `qr_code`                               | `question`                       |
| `quick_login`                        | `radar`                                 | `rain`                           |
| `rain_heavy`                         | `rain_icy`                              | `raindrop`                       |
| `random`                             | `receiver_generic_error_filled`         | `receiver_generic_error_outline` |
| `receiver_generic_filled`            | `receiver_generic_off_filled`           | `receiver_generic_off_outline`   |
| `receiver_generic_outline`           | `receiver_generic_warn_filled`          | `receiver_generic_warn_outline`  |
| `redo`                               | `redo_bold`                             | `refresh`                        |
| `refresh_bold`                       | `remove`                                | `remove_bold`                    |
| `remove_circle`                      | `remove_heavy`                          | `rename_route`                   |
| `reply`                              | `reports`                               | `reroute`                        |
| `reschedule_route`                   | `rewind`                                | `ri`                             |
| `road_surface`                       | `route`                                 | `route_add`                      |
| `route_compliance`                   | `route_delete`                          | `route_load`                     |
| `route_modifiers`                    | `route_off`                             | `route_on`                       |
| `route_optimize`                     | `route_options`                         | `route_save`                     |
| `row_add`                            | `row_copy`                              | `row_cut`                        |
| `row_delete`                         | `row_highlighted`                       | `row_insert_after`               |
| `row_insert_before`                  | `row_paste_after`                       | `row_paste_before`               |
| `row_properties`                     | `row_remove`                            | `rows_show_less`                 |
| `rows_show_more`                     | `rpt`                                   | `rss_feed`                       |
| `rts`                                | `rts_off`                               | `rts_rpt`                        |
| `ruler`                              | `satellite`                             | `save_as`                        |
| `save_disk`                          | `scan_barcode`                          | `schema`                         |
| `school_bus`                         | `scissors`                              | `screen`                         |
| `screenshot`                         | `search`                                | `select_area`                    |
| `server`                             | `server_round`                          | `settings`                       |
| `share`                              | `shield`                                | `shopping_cart`                  |
| `shopping_cart_minus`                | `shopping_cart_plus`                    | `shortcut`                       |
| `shovel`                             | `show_closest`                          | `show_less_caret`                |
| `show_more_caret`                    | `show_truck_info`                       | `sign_in`                        |
| `sign_out`                           | `signal`                                | `site_manager`                   |
| `smiley_dissatisfied`                | `smiley_dissatisfied_outlined`          | `smiley_neutral`                 |
| `smiley_neutral_outlined`            | `smiley_satisfied`                      | `smiley_satisfied_outlined`      |
| `smiley_somewhat_dissatisfied`       | `smiley_somewhat_dissatisfied_outlined` | `smiley_somewhat_satisfied`      |
| `smiley_somewhat_satisfied_outlined` | `snow_heavy`                            | `snow_light`                     |
| `snow_particle`                      | `snowflake`                             | `snowflakes`                     |
| `sort`                               | `sort_alpha_down`                       | `sort_alpha_up`                  |
| `sort_arrow_down`                    | `sort_arrow_up`                         | `sort_down`                      |
| `sort_up`                            | `speed_coaching_profiles`               | `spinner`                        |
| `star`                               | `star_half`                             | `star_locked`                    |
| `star_northern`                      | `star_outlined`                         | `stars`                          |
| `stop_circle`                        | `stop_details`                          | `stop_summary`                   |
| `stop_time`                          | `street_measurement`                    | `submit_expense`                 |
| `suggestion`                         | `sun`                                   | `swatch`                         |
| `swap`                               | `switch_account`                        | `switch_left`                    |
| `switch_right`                       | `sync`                                  | `sync_bold`                      |
| `sync_filled`                        | `sync_off`                              | `sx10`                           |
| `table`                              | `tablet`                                | `tag`                            |
| `tag_disabled`                       | `template`                              | `text_align_left`                |
| `text_align_right`                   | `text_bold`                             | `text_centered`                  |
| `text_grow`                          | `text_input`                            | `text_input_long`                |
| `text_input_short`                   | `text_italic`                           | `text_marker`                    |
| `text_shrink`                        | `text_strikethrough`                    | `text_truncated`                 |
| `text_underlined`                    | `thermometer_cold`                      | `thermometer_hot`                |
| `thumbs_down`                        | `thumbs_up`                             | `thunderstorm_heavy`             |
| `thunderstorm_light`                 | `ticket`                                | `ticket_plane`                   |
| `time_off_work`                      | `time_slot_not_reserved`                | `time_slot_reserved`             |
| `timer`                              | `timer_countdown`                       | `timesheet`                      |
| `timesheet_approve`                  | `todo`                                  | `todo_add`                       |
| `toggle`                             | `toggle_center`                         | `toggle_left_panel`              |
| `toggle_off`                         | `toggle_on`                             | `toggle_right_panel`             |
| `total_station`                      | `total_station_lost`                    | `traffic`                        |
| `traffic_cone`                       | `traffic_historical`                    | `train`                          |
| `trash`                              | `tree_structure`                        | `triangle_down`                  |
| `triangle_left`                      | `triangle_right`                        | `triangle_up`                    |
| `trim_fake_orders`                   | `trimble_logo`                          | `truck`                          |
| `truck_add`                          | `truck_warning_delay`                   | `tune`                           |
| `tune_circle`                        | `turn_dispatch_mode_on`                 | `two_way`                        |
| `unarchive_square`                   | `uncombine`                             | `undo`                           |
| `undo_bold`                          | `unfold_less`                           | `unfold_more`                    |
| `unit_selector`                      | `unload_route_stop`                     | `unloaded_order`                 |
| `unloaded_orders`                    | `unsorted_arrows`                       | `update`                         |
| `upgrade_modifiers`                  | `upload`                                | `upload_xls`                     |
| `user`                               | `user_account`                          | `user_active`                    |
| `user_fields`                        | `user_guide`                            | `user_inactive`                  |
| `user_passkey`                       | `user_permissions`                      | `vehicle_groups`                 |
| `vertical_accuracy`                  | `video`                                 | `video_add`                      |
| `video_disabled`                     | `view_2_rows`                           | `view_3_column`                  |
| `view_grid`                          | `view_list`                             | `visibility`                     |
| `visibility_off`                     | `visibility_on`                         | `visibility_part_outline`        |
| `volume_down`                        | `volume_mute`                           | `volume_up`                      |
| `volumes`                            | `vr_xr`                                 | `warehouse`                      |
| `warning`                            | `warning_outlined`                      | `weather_alerts`                 |
| `web`                                | `wheelbarrow`                           | `widgets`                        |
| `wifi`                               | `wifi_no_internet`                      | `wifi_off`                       |
| `wind`                               | `window`                                | `window_dock_undock`             |
| `window_fit`                         | `window_resize`                         | `window_side_panel`              |
| `window_template`                    | `window_views`                          | `window_wireframe`               |
| `wintery_mix`                        | `workers_queue`                         | `wrench`                         |
| `x12`                                | `x7`                                    | `x7_card`                        |
| `x7_settings`                        | `xr10`                                  | `zoom_box`                       |
| `zoom_center`                        | `zoom_in`                               | `zoom_out`                       |

---

### Theme & Style Reference

The following sections detail the specific style properties available in the Modus Classic themes.

### Shared Base Values (Inherited by Classic Themes)

These properties are foundational and apply to both `modus-classic-light` and `modus-classic-dark`.

#### **Spacing**

- `--modus-wc-spacing-2xs`: `0.125rem`
- `--modus-wc-spacing-xs`: `0.25rem`
- `--modus-wc-spacing-sm`: `0.5rem`
- `--modus-wc-spacing-md`: `0.75rem`
- `--modus-wc-spacing-lg`: `1rem`
- `--modus-wc-spacing-xl`: `1.5rem`
- `--modus-wc-spacing-2xl`: `2rem`
- `--modus-wc-spacing-3xl`: `3rem`

#### **Sizing (Font, Input, Border Width)**

- **Font Sizes:**
  - `--modus-wc-font-size-sm`: `0.75rem`
  - `--modus-wc-font-size-md`: `0.875rem`
  - `--modus-wc-font-size-lg`: `1rem`
  - `--modus-wc-font-size-xl`: `1.125rem`
  - `--modus-wc-font-size-2xl`: `1.25rem`
  - `--modus-wc-font-size-3xl`: `1.5rem`
- **Input Heights:**
  - `--modus-wc-input-height-sm`: `1.5rem`
  - `--modus-wc-input-height-md`: `2rem`
  - `--modus-wc-input-height-lg`: `3rem`
- **Border Widths:**
  - `--modus-wc-border-width-xs`: `1px`
  - `--modus-wc-border-width-sm`: `2px`
  - `--modus-wc-border-width-md`: `3px`
  - `--modus-wc-border-width-lg`: `4px`
  - `--modus-wc-border-width-xl`: `8px`
- **Other Component Sizing:**
  - `--tab-border`: `1px`

#### **Radius (Base Defaults)**

- `--modus-wc-border-radius-sm`: `2px`
- `--modus-wc-border-radius-md`: `4px`
- `--modus-wc-border-radius-lg`: `8px`
- `--modus-wc-border-radius-xl`: `12px`
- `--rounded-badge`: `0.25rem`
- `--tab-radius`: `0.5rem`

#### **Shadows**

Shadows are applied via utility classes rather than theme-specific variables.

- **Button Shadow (`.modus-wc-btn`):** `0 1px 2px 0 rgba(0, 0, 0, 0.05)`
- **Modal Box Shadow (`.modus-wc-modal-box`):** `0 25px 50px -12px rgba(0, 0, 0, 0.25)`

#### **Breakpoints**

Breakpoints are used for Modus responsiveness.

| Name    | Value  |
| :------ | :----- |
| **xxs** | 320px  |
| **xs**  | 390px  |
| **sm**  | 640px  |
| **md**  | 768px  |
| **lg**  | 1024px |
| **xl**  | 1280px |
| **xxl** | 1536px |

---

### Modus Classic Light `[data-theme="modus-classic-light"]`

#### **Colors**

- `--modus-wc-color-base-page`: `#fff` (white)
- `--modus-wc-color-base-100`: `#f1f1f6` (gray-light)
- `--modus-wc-color-base-200`: `#cbcdd6` (gray-1)
- `--modus-wc-color-base-300`: `#b7b9c3` (gray-2)
- `--modus-wc-color-base-content`: `#171c1e` (gray-10)
- `--modus-wc-color-info`: `#0063a3` (trimble-blue)
- `--modus-wc-color-success`: `#1e8a44` (green)
- `--modus-wc-color-error`: `#da212c` (red)
- `--modus-wc-color-warning`: `#fbad26` (yellow)
- `primary-focus`: `#004f83`
- `secondary-focus`: `#464b52`
- `accent-focus`: `#464b52`
- `neutral-focus`: `#a3a6b1`

#### **Radius**

- `--rounded-btn`: `0.25rem`
- `--rounded-box`: `0.5rem`

---

### Modus Classic Dark `[data-theme="modus-classic-dark"]`

#### **Colors**

- `--modus-wc-color-base-page`: `#000` (black)
- `--modus-wc-color-base-100`: `#252a2e` (trimble-gray)
- `--modus-wc-color-base-200`: `#464b52` (gray-8)
- `--modus-wc-color-base-300`: `#353a40` (gray-9)
- `--modus-wc-color-base-content`: `#cbcdd6` (gray-1)
- `--modus-wc-color-info`: `#0063a3` (trimble-blue)
- `--modus-wc-color-success`: `#1e8a44` (green)
- `--modus-wc-color-error`: `#da212c` (red)
- `--modus-wc-color-warning`: `#fbad26` (yellow)
- `primary-focus`: `#004f83`
- `secondary-focus`: `#e49325`
- `accent-focus`: `#464b52`
- `neutral-focus`: `#171c1e`

#### **Radius**

- `--rounded-btn`: `0.25rem`
- `--rounded-box`: `0.5rem`

---

### Fallback Colors for Older Browsers

These colors are used automatically for browsers that do not support modern CSS color functions like `oklch`.

#### **Fallback for Light Theme**

- **Primary:** `#491eff` (fg: `#d4dbff`)
- **Secondary:** `#ff41c7` (fg: `#fff9fc`)
- **Accent:** `#00cfbd` (fg: `#00100d`)
- **Neutral:** `#2b3440` (fg: `#d7dde4`)
- **Base-100:** `#fff`
- **Base-200/300:** `#e5e6e6`
- **Base Content:** `#1f2937`
- **Info:** `#00b3f0` (fg: `#000`)
- **Success:** `#00ca92` (fg: `#000`)
- **Warning:** `#ffc22d` (fg: `#000`)
- **Error:** `#ff6f70` (fg: `#000`)

#### **Fallback for Dark Theme**

- **Primary:** `#7582ff` (fg: `#050617`)
- **Secondary:** `#ff71cf` (fg: `#190211`)
- **Accent:** `#00c7b5` (fg: `#000e0c`)
- **Neutral:** `#2a323c` (fg: `#a6adbb`)
- **Base-100:** `#1d232a`
- **Base-200:** `#191e24`
- **Base-300:** `#15191e`
- **Base Content:** `#a6adbb`
- **Info:** `#00b3f0` (fg: `#000`)
- **Success:** `#00ca92` (fg: `#000`)
- **Warning:** `#ffc22d` (fg: `#000`)
- **Error:** `#ff6f70` (fg: `#000`)
