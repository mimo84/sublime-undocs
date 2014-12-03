

.. module:: sublime

.. function:: Methods

   Description

   :rtype: Return Value

.. function:: set_timeout(callback, delay)

.. function:: set_async_timeout(callback, delay)

.. function:: status_message(string)

.. function:: error_message(string)

.. function:: message_dialog(string)

.. function:: ok_cancel_dialog(string, <ok_button>)

   Displays an ok / cancel question dialog to the user. If ok_button
   is provided, this may be used as the text on the ok
   button. Returns True if the user presses the ok button.

   :rtype: bool

.. function:: load_resource(name)

   Loads the given resource. The name should be in the format Packages/Default/Main.sublime-menu.

   :rtype: String

.. function:: load_binary_resource(name)

   Loads the given resource. The name should be in the format Packages/Default/Main.sublime-menu.

   :rtype: bytes

.. function:: find_resources(pattern)

   Finds resources whose file name matches the given pattern.

   :rtype: [String]

.. function:: encode_value(value, <pretty>)

   Encode a JSON compatible value into a string representation. If pretty is
   set to True, the string will include newlines and indentation.

   :rtype: String

.. function:: decode_value(string)

   Decodes a JSON string into an object. If the string is invalid,
   a ValueError will be thrown.

   :rtype: value

.. function:: load_settings(base_name)

   Loads the named settings. The name should include a file name and
   extension, but not a path. The packages will be searched for files
   matching the base name, and the results will be collated into the
   settings object. Subsequent calls to load_settings with the name base_name will return
   the same object, and not load the settings from disk again.

   :rtype: Settings

.. function:: save_settings(base_name)

.. function:: windows()

   Returns a list of all the open windows.

   :rtype: [Window]

.. function:: active_window()

   Returns the most recently used window.

   :rtype: Window

.. function:: packages_path()

   Returns the base path to the packages.

   :rtype: String

.. function:: installed_packages_path()

   Returns the path where all the user's *.sublime-package files are.

   :rtype: String

.. function:: cache_path()

   Returns the path where Sublime Text stores cache files.

   :rtype: String

.. function:: get_clipboard(<size_limit>)

   Returns the contents of the clipboard. size_limit is there to protect against
   unnecessarily large data, defaults to 16,777,216 characters

   :rtype: String

.. function:: set_clipboard(string)

.. function:: score_selector(scope, selector)

   Matches the selector against the given scope, returning a score. A score
   of 0 means no match, above 0 means a match. Different selectors
   may be compared against the same scope: a higher score means the
   selector is a better match for the scope.

   :rtype: Int

.. function:: run_command(string, <args>)

.. function:: log_commands(flag)

.. function:: log_input(flag)

.. function:: log_result_regex(flag)

.. function:: version()

   Returns the version number

   :rtype: String

.. function:: platform()

   Returns the platform, which may be "osx", "linux" or "windows"

   :rtype: String

.. function:: arch()

   Returns the CPU architecture, which may be "x32" or "x64"

   :rtype: String

.. class:: sublime.View

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: id()

      Returns a number that uniquely identifies this view.

      :rtype: int

   .. method:: buffer_id()

      Returns a number that uniquely identifies the buffer underlying this view.

      :rtype: int

   .. method:: file_name()

      The full name file the file associated with the buffer, or None
      if it doesn't exist on disk.

      :rtype: String

   .. method:: name()

      The name assigned to the buffer, if any

      :rtype: String

   .. method:: set_name(name)

   .. method:: is_loading()

      Returns true if the buffer is still loading from disk, and not
      ready for use.

      :rtype: bool

   .. method:: is_dirty()

      Returns true if there are any unsaved modifications to the buffer.

      :rtype: bool

   .. method:: is_read_only()

      Returns true if the buffer may not be modified.

      :rtype: bool

   .. method:: set_read_only(value)

   .. method:: is_scratch()

      Returns true if the buffer is a scratch buffer. Scratch buffers never
      report as being dirty.

      :rtype: bool

   .. method:: set_scratch(value)

   .. method:: settings()

      Returns a reference to the views settings object. Any changes to this
      settings object will be private to this view.

      :rtype: Settings

   .. method:: window()

      Returns a reference to the window containing the view.

      :rtype: Window

   .. method:: run_command(string, <args>)

   .. method:: size()

      Returns the number of character in the file.

      :rtype: int

   .. method:: substr(region)

      Returns the contents of the region as a string.

      :rtype: String

   .. method:: substr(point)

      Returns the character to the right of the point.

      :rtype: String

   .. method:: insert(edit, point, string)

      Inserts the given string in the buffer at the specified point. Returns
      the number of characters inserted: this may be different if tabs are
      being translated into spaces in the current buffer.

      :rtype: int

   .. method:: erase(edit, region)

   .. method:: replace(edit, region, string)

   .. method:: sel()

      Returns a reference to the selection.

      :rtype: Selection

   .. method:: line(point)

      Returns the line that contains the point.

      :rtype: Region

   .. method:: line(region)

      Returns a modified copy of region such that it starts at the
      beginning of a line, and ends at the end of a line.
      Note that it may span several lines.

      :rtype: Region

   .. method:: full_line(point)

      As line(), but the region includes the trailing newline character, if any.

      :rtype: Region

   .. method:: full_line(region)

      As line(), but the region includes the trailing newline character, if any.

      :rtype: Region

   .. method:: lines(region)

      Returns a list of lines (in sorted order) intersecting the region.

      :rtype: [Region]

   .. method:: split_by_newlines(region)

      Splits the region up such that each region returned exists on exactly
      one line.

      :rtype: [Region]

   .. method:: word(point)

      Returns the word that contains the point.

      :rtype: Region

   .. method:: word(region)

      Returns a modified copy of region such that it starts at the
      beginning of a word, and ends at the end of a word.
      Note that it may span several words.

      :rtype: Region

   .. method:: classify(point)

      Classifies pt, returning a bitwise OR of zero or more of these
      flags: CLASS_WORD_START CLASS_WORD_END CLASS_PUNCTUATION_START CLASS_PUNCTUATION_END CLASS_SUB_WORD_START CLASS_SUB_WORD_END CLASS_LINE_START CLASS_LINE_END CLASS_EMPTY_LINE

      :rtype: int

   .. method:: find_by_class(point, forward, classes, <separators>)

      Finds the next location after point that matches the given classes. If
      forward is False, searches backwards instead of forwards. classes is a bitwise
      OR of the sublime.CLASS_XXX flags. separators may be passed in, to define
      what characters should be considered to separate words.

      :rtype: Region

   .. method:: expand_by_class(point, classes, <separators>)

      Expands point to the left and right, until each side lands on
      a location that matches classes. classes is a bitwise OR of the
      sublime.CLASS_XXX flags. separators may be passed in, to define what characters should
      be considered to separate words.

      :rtype: Region

   .. method:: expand_by_class(region, classes, <separators>)

      Expands region to the left and right, until each side lands on
      a location that matches classes. classes is a bitwise OR of the
      sublime.CLASS_XXX flags. separators may be passed in, to define what characters should
      be considered to separate words.

      :rtype: Region

   .. method:: find(pattern, fromPosition, <flags>)

      Returns the first Region matching the regex pattern, starting from the given
      point, or None if it can't be found. The optional flags parameter
      may be sublime.LITERAL, sublime.IGNORECASE, or the two ORed together.

      :rtype: Region

   .. method:: find_all(pattern, <flags>, <format>, <extractions>)

      Returns all (non-overlapping) regions matching the regex pattern. The optional flags parameter
      may be sublime.LITERAL, sublime.IGNORECASE, or the two ORed together. If a format
      string is given, then all matches will be formatted with the formatted
      string and placed into the extractions list.

      :rtype: [Region]

   .. method:: rowcol(point)

      Calculates the 0 based line and column numbers of the point.

      :rtype: (int, int)

   .. method:: text_point(row, col)

      Calculates the character offset of the given, 0 based, row and column.
      Note that 'col' is interpreted as the number of characters to advance
      past the beginning of the row.

      :rtype: int

   .. method:: set_syntax_file(syntax_file)

   .. method:: extract_scope(point)

      Returns the extent of the syntax name assigned to the character at
      the given point.

      :rtype: Region

   .. method:: scope_name(point)

      Returns the syntax name assigned to the character at the given point.

      :rtype: String

   .. method:: score_selector(point, selector)

      Matches the selector against the scope at the given location, returning a
      score. A score of 0 means no match, above 0 means a
      match. Different selectors may be compared against the same scope: a higher
      score means the selector is a better match for the scope.

      :rtype: Int

   .. method:: find_by_selector(selector)

      Finds all regions in the file matching the given selector, returning them
      as a list.

      :rtype: [Regions]

   .. method:: show(point, <show_surrounds>)

   .. method:: show(region, <show_surrounds>)

   .. method:: show(region_set, <show_surrounds>)

   .. method:: show_at_center(point)

   .. method:: show_at_center(region)

   .. method:: visible_region()

      Returns the currently visible area of the view.

      :rtype: Region

   .. method:: viewport_position()

      Returns the offset of the viewport in layout coordinates.

      :rtype: Vector

   .. method:: set_viewport_position(vector, <animate<)

   .. method:: viewport_extent()

      Returns the width and height of the viewport.

      :rtype: vector

   .. method:: layout_extent()

      Returns the width and height of the layout.

      :rtype: vector

   .. method:: text_to_layout(point)

      Converts a text position to a layout position

      :rtype: vector

   .. method:: layout_to_text(vector)

      Converts a layout position to a text position

      :rtype: point

   .. method:: window_to_layout(vector)

      Converts a window position to a layout position

      :rtype: vector

   .. method:: window_to_text(vector)

      Converts a window position to a text position

      :rtype: point

   .. method:: line_height()

      Returns the light height used in the layout

      :rtype: real

   .. method:: em_width()

      Returns the typical character width used in the layout

      :rtype: real

   .. method:: add_regions(key, [regions], <scope>, <icon>, <flags>)

   .. method:: get_regions(key)

      Return the regions associated with the given key, if any

      :rtype: [regions]

   .. method:: erase_regions(key)

   .. method:: set_status(key, value)

   .. method:: get_status(key)

      Returns the previously assigned value associated with the key, if any.

      :rtype: String

   .. method:: erase_status(key)

   .. method:: command_history(index, <modifying_only>)

      Returns the command name, command arguments, and repeat count for the given
      history entry, as stored in the undo / redo stack. Index 0
      corresponds to the most recent command, -1 the command before that, and
      so on. Positive values for index indicate to look in the redo
      stack for commands. If the undo / redo history doesn't extend far
      enough, then (None, None, 0) will be returned. Setting modifying_only to True
      (the default is False) will only return entries that modified the buffer.

      :rtype: (String,Dict,int)

   .. method:: change_count()

      Returns the current change count. Each time the buffer is modified, the
      change count is incremented. The change count can be used to determine
      if the buffer has changed since the last it was inspected.

      :rtype: int

   .. method:: fold([regions])

      Folds the given regions, returning False if they were already folded

      :rtype: bool

   .. method:: fold(region)

      Folds the given region, returning False if it was already folded

      :rtype: bool

   .. method:: unfold(region)

      Unfolds all text in the region, returning the unfolded regions

      :rtype: [regions]

   .. method:: unfold([regions])

      Unfolds all text in the regions, returning the unfolded regions

      :rtype: [regions]

   .. method:: encoding()

      Returns the encoding currently associated with the file

      :rtype: String

   .. method:: set_encoding(encoding)

   .. method:: line_endings()

      Returns the line endings used by the current file.

      :rtype: String

   .. method:: set_line_endings(line_endings)

   .. method:: overwrite_status()

      Returns the overwrite status, which the user normally toggles via the insert
      key.

      :rtype: Bool

   .. method:: set_overwrite_status(enabled)

   .. method:: symbols(line_endings)

      Extract all the symbols defined in the buffer.

      :rtype: [(Region, String)]

   .. method:: show_popup_menu(items, on_done, <flags>)

.. class:: sublime.Selection

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: clear()

   .. method:: add(region)

   .. method:: add_all(region_set)

   .. method:: subtract(region)

   .. method:: contains(region)

      Returns true iff the given region is a subset.

      :rtype: bool

.. class:: sublime.Region

   .. method:: Constructors

      n/a

      :rtype: Description

   .. method:: Region(a, b)

      n/a

      :rtype: Creates a Region with initial values a and b.

.. class:: sublime.Edit

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: (no methods)



      :rtype: 

.. class:: sublime.Window

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: id()

      Returns a number that uniquely identifies this window.

      :rtype: int

   .. method:: new_file()

      Creates a new file. The returned view will be empty, and its
      is_loaded method will return True.

      :rtype: View

   .. method:: open_file(file_name, <flags>)

      Opens the named file, and returns the corresponding view. If the file
      is already opened, it will be brought to the front. Note that
      as file loading is asynchronous, operations on the returned view won't be
      possible until its is_loading() method returns False. The optional flags parameter is
      a bitwise combination of: sublime.ENCODED_POSITION. Indicates the file_name should be searched for
      a :row or :row:col suffix sublime.TRANSIENT. Open the file as a preview
      only: it won't have a tab assigned it until modified

      :rtype: View

   .. method:: find_open_file(file_name)

      Finds the named file in the list of open files, and returns
      the corresponding View, or None if no such file is open.

      :rtype: View

   .. method:: active_view()

      Returns the currently edited view.

      :rtype: View

   .. method:: active_view_in_group(group)

      Returns the currently edited view in the given group.

      :rtype: View

   .. method:: views()

      Returns all open views in the window.

      :rtype: [View]

   .. method:: views_in_group(group)

      Returns all open views in the given group.

      :rtype: [View]

   .. method:: num_groups()

      Returns the number of view groups in the window.

      :rtype: int

   .. method:: active_group()

      Returns the index of the currently selected group.

      :rtype: int

   .. method:: focus_group(group)

   .. method:: focus_view(view)

   .. method:: get_view_index(view)

      Returns the group, and index within the group of the view. Returns
      -1 if not found.

      :rtype: (group, index)

   .. method:: set_view_index(view, group, index)

   .. method:: folders()

      Returns a list of the currently open folders.

      :rtype: [String]

   .. method:: project_file_name()

      Returns name of the currently opened project file, if any.

      :rtype: String

   .. method:: project_data()

      Returns the project data associated with the current window. The data is
      in the same format as the contents of a .sublime-project file. set_project_data(data)NoneUpdates
      the project data associated with the current window. If the window is
      associated with a .sublime-project file, the project file will be updated on
      disk, otherwise the window will store the data internally. run_command(string, <args>)NoneRuns the
      named Command with the (optional) given arguments. Window.run_command is able to run
      both any sort of command, dispatching the command via input focus. show_quick_panel(items,
      on_done, <flags>, <selected_index>, <on_highlighted>)NoneShows a quick panel, to select an item in
      a list. on_done will be called once, with the index of the
      selected item. If the quick panel was cancelled, on_done will be called
      with an argument of -1. Items may be an array of strings,
      or an array of string arrays. In the latter case, each entry
      in the quick panel will show multiple rows. Flags currently only has
      one option, sublime.MONOSPACE_FONT on_highlighted, if given, will be called every time the
      highlighted item in the quick panel is changed. show_input_panel(caption, initial_text, on_done, on_change,
      on_cancel)ViewShows the input panel, to collect a line of input from the
      user. on_done and on_change, if not None, should both be functions that
      expect a single string argument. on_cancel should be a function that expects
      no arguments. The view used for the input widget is returned. create_output_panel(name)ViewReturns
      the view associated with the named output panel, created it if required.
      The output panel can be shown by running the show_panel window command,
      with the panel argument set to the name with an "output." prefix.
      lookup_symbol_in_index(symbol)[Location]Returns all locations where the symbol is defined across files in the
      current project. lookup_symbol_in_open_files(symbol)[Location]Returns all locations where the symbol is defined across open
      files.

      :rtype: Dictionary

   .. method:: set_project_data(data)

   .. method:: run_command(string, <args>)

   .. method:: show_quick_panel(items, on_done, <flags>, <selected_index>, <on_highlighted>)

   .. method:: show_input_panel(caption, initial_text, on_done, on_change, on_cancel)

      Shows the input panel, to collect a line of input from the
      user. on_done and on_change, if not None, should both be functions that
      expect a single string argument. on_cancel should be a function that expects
      no arguments. The view used for the input widget is returned.

      :rtype: View

   .. method:: create_output_panel(name)

      Returns the view associated with the named output panel, created it if
      required. The output panel can be shown by running the show_panel window
      command, with the panel argument set to the name with an "output."
      prefix. lookup_symbol_in_index(symbol)[Location]Returns all locations where the symbol is defined across files in
      the current project. lookup_symbol_in_open_files(symbol)[Location]Returns all locations where the symbol is defined across
      open files.

      :rtype: View

   .. method:: lookup_symbol_in_index(symbol)

      Returns all locations where the symbol is defined across files in the
      current project.

      :rtype: [Location]

   .. method:: lookup_symbol_in_open_files(symbol)

      Returns all locations where the symbol is defined across open files.

      :rtype: [Location]

.. class:: sublime.Settings

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: get(name)

      Returns the named setting.

      :rtype: value

   .. method:: get(name, default)

      Returns the named setting, or default if it's not defined.

      :rtype: value

   .. method:: set(name, value)

   .. method:: erase(name)

   .. method:: has(name)

      Returns true iff the named option exists in this set of Settings
      or one of its parents.

      :rtype: bool

   .. method:: add_on_change(key, on_change)

   .. method:: clear_on_change(key)

.. module:: sublime_plugin

.. function:: Methods

   Description

   :rtype: Return Value

.. function:: (no methods)



   :rtype: 

.. class:: sublime_plugin.EventListener

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: on_new(view)

   .. method:: on_new_async(view)

   .. method:: on_clone(view)

   .. method:: on_clone_async(view)

   .. method:: on_load(view)

   .. method:: on_load_async(view)

   .. method:: on_pre_close(view)

   .. method:: on_close(view)

   .. method:: on_pre_save(view)

   .. method:: on_pre_save_async(view)

   .. method:: on_post_save(view)

   .. method:: on_post_save_async(view)

   .. method:: on_modified(view)

   .. method:: on_modified_async(view)

   .. method:: on_selection_modified(view)

   .. method:: on_selection_modified_async(view)

   .. method:: on_activated(view)

   .. method:: on_activated_async(view)

   .. method:: on_deactivated(view)

   .. method:: on_deactivated_async(view)

   .. method:: on_text_command(view, command_name, args)

      Called when a text command is issued. The listener may return a
      (command, arguments) tuple to rewrite the command, or None to run the
      command unmodified.

      :rtype: (new_command_name, new_args)

   .. method:: on_window_command(window, command_name, args)

      Called when a window command is issued. The listener may return a
      (command, arguments) tuple to rewrite the command, or None to run the
      command unmodified.

      :rtype: (new_command_name, new_args)

   .. method:: post_text_command(view, command_name, args)

   .. method:: post_window_command(window, command_name, args)

   .. method:: on_query_context(view, key, operator, operand, match_all)

      Called when determining to trigger a key binding with the given context
      key. If the plugin knows how to respond to the context, it
      should return either True of False. If the context is unknown, it
      should return None. operator is one of: sublime.OP_EQUAL. Is the value of
      the context equal to the operand? sublime.OP_NOT_EQUAL. Is the value of the
      context not equal to the operand? sublime.OP_REGEX_MATCH. Does the value of the
      context match the regex given in operand? sublime.OP_NOT_REGEX_MATCH. Does the value of
      the context not match the regex given in operand? sublime.OP_REGEX_CONTAINS. Does the
      value of the context contain a substring matching the regex given in
      operand? sublime.OP_NOT_REGEX_CONTAINS. Does the value of the context not contain a substring
      matching the regex given in operand? match_all should be used if the
      context relates to the selections: does every selection have to match (match_all
      = True), or is at least one matching enough (match_all = Fals)?

      :rtype: bool or None

.. class:: sublime_plugin.ApplicationCommand

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: run(<args>)

   .. method:: is_enabled(<args>)

      Returns true if the command is able to be run at this
      time. The default implementation simply always returns True.

      :rtype: bool

   .. method:: is_visible(<args>)

      Returns true if the command should be shown in the menu at
      this time. The default implementation always returns True.

      :rtype: bool

   .. method:: is_checked(<args>)

      Returns true if a checkbox should be shown next to the menu
      item. The .sublime-menu file must have the checkbox attribute set to true
      for this to be used.

      :rtype: bool

   .. method:: description(<args>)

      Returns a description of the command with the given arguments. Used in
      the menu, if no caption is provided. Return None to get the
      default description.

      :rtype: String

.. class:: sublime_plugin.WindowCommand

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: run(<args>)

   .. method:: is_enabled(<args>)

      Returns true if the command is able to be run at this
      time. The default implementation simply always returns True.

      :rtype: bool

   .. method:: is_visible(<args>)

      Returns true if the command should be shown in the menu at
      this time. The default implementation always returns True.

      :rtype: bool

   .. method:: description(<args>)

      Returns a description of the command with the given arguments. Used in
      the menu, if no caption is provided. Return None to get the
      default description.

      :rtype: String

.. class:: sublime_plugin.TextCommand

   .. method:: Methods

      Description

      :rtype: Return Value

   .. method:: run(edit, <args>)

   .. method:: is_enabled(<args>)

      Returns true if the command is able to be run at this
      time. The default implementation simply always returns True.

      :rtype: bool

   .. method:: is_visible(<args>)

      Returns true if the command should be shown in the menu at
      this time. The default implementation always returns True.

      :rtype: bool

   .. method:: description(<args>)

      Returns a description of the command with the given arguments. Used in
      the menus, and for Undo / Redo descriptions. Return None to get
      the default description.

      :rtype: String

   .. method:: want_event()

      Return True to receive an event argument when the command is triggered
      by a mouse action. The event information allows commands to determine which
      portion of the view was clicked on. The default implementation returns False.

      :rtype: bool
