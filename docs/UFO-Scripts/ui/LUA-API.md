## global functions

    function ufo.findvar(string varName)
    function ufo.getvar(string var_name, string var_value, int flags, string desc)
    function ufo.getvar(string var_name, string var_value, int flags)
    function ufo.getvar(string var_name, string var_value)
    function ufo.getvar(string var_name)
    function ufo.create_control(uiNode parent, string type, string name, string super)
    function ufo.create_bar(uiNode parent, string name, string super)
    function ufo.create_button(uiNode parent, string name, string super)
    function ufo.create_basemap(uiNode parent, string name, string super)
    function ufo.create_baselayout(uiNode parent, string name, string super)
    function ufo.create_baseinventory(uiNode parent, string name, string super)
    function ufo.create_checkbox(uiNode parent, string name, string super)
    function ufo.create_confunc(uiNode parent, string name, string super)
    function ufo.create_container(uiNode parent, string name, string super)
    function ufo.create_data(uiNode parent, string name, string super)
    function ufo.create_ekg(uiNode parent, string name, string super)
    function ufo.create_geoscape(uiNode parent, string name, string super)
    function ufo.create_image(uiNode parent, string name, string super)
    function ufo.create_item(uiNode parent, string name, string super)
    function ufo.create_linechart(uiNode parent, string name, string super)
    function ufo.create_messagelist(uiNode parent, string name, string super)
    function ufo.create_model(uiNode parent, string name, string super)
    function ufo.create_option(uiNode parent, string name, string super)
    function ufo.create_optionlist(uiNode parent, string name, string super)
    function ufo.create_optiontree(uiNode parent, string name, string super)
    function ufo.create_panel(uiNode parent, string name, string super)
    function ufo.create_radar(uiNode parent, string name, string super)
    function ufo.create_radiobutton(uiNode parent, string name, string super)
    function ufo.create_rows(uiNode parent, string name, string super)
    function ufo.create_selectbox(uiNode parent, string name, string super)
    function ufo.create_sequence(uiNode parent, string name, string super)
    function ufo.create_spinner(uiNode parent, string name, string super)
    function ufo.create_string(uiNode parent, string name, string super)
    function ufo.create_tab(uiNode parent, string name, string super)
    function ufo.create_tbar(uiNode parent, string name, string super)
    function ufo.create_text(uiNode parent, string name, string super)
    function ufo.create_text2(uiNode parent, string name, string super)
    function ufo.create_textentry(uiNode parent, string name, string super)
    function ufo.create_textlist(uiNode parent, string name, string super)
    function ufo.create_texture(uiNode parent, string name, string super)
    function ufo.create_timer(uiNode parent, string name, string super)
    function ufo.create_video(uiNode parent, string name, string super)
    function ufo.create_vscrollbar(uiNode parent, string name, string super)
    function ufo.create_widget(uiNode parent, string name, string super)
    function ufo.create_window(string name, string super)
    function ufo.create_zone(string name, string super)
    function ufo.create_component(string type, string name, string super)
    function ufo.pop_window(bool all)
    function ufo.push_window(string name, string parentName,  params)
    function ufo.cmd(string command)
    function ufo.print(string fmt)
    function ufo.dprint(int level, string fmt)
    function ufo.error(int code, string fmt)
    function ufo.nodetree(uiNode node)
    function ufo.register_onload(LUA_FUNCTION fcn)

## global classes

    class ufo.uiScroll:
        int viewpos ()
        int viewsize ()
        bool fullsize ()
        void set_fullsize (bool value)
        bool set_values (int pos, int size, bool full)
        bool moveto (int pos)
        bool movedelta (int delta)


    class ufo.cvar:
        char name ()
        char as_string ()
        float as_float ()
        int as_integer ()
        void set_value (float number)


    class ufo.invDef:
        char name ()


    class ufo.uiNode:
        bool is_window ()
        bool is_disabled ()
        bool is_invisible ()
        bool is_ghost ()
        bool is_flashing ()
        bool is_function ()
        bool is_virtual ()
        bool is_abstract ()
        float left ()
        float top ()
        float widht ()
        float height ()
        int bordersize ()
        char name ()
        char type ()
        char text ()
        char font ()
        char image ()
        int contentalign ()
        int layoutalign ()
        float flashspeed ()
        int padding ()
        uiNode_t first ()
        uiNode_t last ()
        uiNode_t next ()
        uiNode_t parent ()
        uiNode_t root ()
        uiNode_t child (string name)
        uiNode_t find (string name)
        void append_node (uiNode node)
        void insert_node (uiNode node, uiNode prev)
        void set_left (float value)
        void set_top (float value)
        void set_widht (float value)
        void set_height (float value)
        void set_box (float left, float top, float width, float height)
        void set_flashing (bool value)
        void set_flashspeed (float value)
        void set_invisible (bool value)
        void set_ghost (bool value)
        void set_pos (float x, float y)
        void set_size (float w, float h)
        void set_color (float r, float g, float b, float a)
        void set_disabledcolor (float r, float g, float b, float a)
        void set_flashcolor (float r, float g, float b, float a)
        void set_selectcolor (float r, float g, float b, float a)
        void set_backgroundcolor (float r, float g, float b, float a)
        void set_bordersize (int size)
        void set_bordercolor (float r, float g, float b, float a)
        void set_text (string text)
        void set_font (string name)
        void set_image (string name)
        void set_contentalign (int value)
        void set_layoutalign (int value)
        void set_tooltip (string text)
        void set_disabled (bool value)
        void set_borderthickness (int value)
        void set_padding (int value)
        void __setitem (string name, LUA_METHOD fcn)
        LUA_METHOD __getitem (string name)
        void add_classmethod (string name, LUA_METHOD fcn)
        void add_nodemethod (string name, LUA_METHOD fcn)


    class ufo.uiAbstractOptionNode: uiNode
        int dataid ()
        int count ()
        void set_dataid (string name)
        void set_background (string name)
        LUA_EVENT on_viewchange ()


    class ufo.uiAbstractScrollableNode: uiNode
        int viewpos ()
        int viewsize ()
        int fullsize ()
        void pageup ()
        void pagedown ()
        void moveup ()
        void movedown ()
        void movehome ()
        void moveend ()
        void set_viewpos (int pos)
        void set_viewsize (int size)
        void set_fullsize (int size)
        LUA_EVENT on_viewchange ()


    class ufo.uiAbstractScrollbarNode: uiNode
        bool is_autoshowscroll ()
        int current ()
        int viewsize ()
        int fullsize ()
        void set_autoshowscroll (bool value)
        void set_current (int pos)
        void set_viewsize (int size)
        void set_fullsize (int size)


    class ufo.uiAbstractValueNode: uiNode
        float min ()
        float max ()
        float value ()
        float delta ()
        float lastdiff ()
        float shiftmultiplier ()
        void inc_value ()
        void dec_value ()
        void set_range (float min, float max)
        void set_range (string min, string max)
        void set_min (float min)
        void set_max (float max)
        void set_value (float value)
        void set_min (string min)
        void set_max (string max)
        void set_value (string name)


    class ufo.uiBar: uiAbstractValueNode
        bool is_readonly ()
        bool is_nohover ()
        int direction ()
        void set_direction (int value)
        void set_readonly (bool value)
        void set_nohover (bool value)


    class ufo.uiAbstractBase: uiNode
        int baseid ()


    class ufo.uiBaseMap: uiAbstractBase


    class ufo.uiBaseLayout: uiAbstractBase


    class ufo.uiButton: uiNode
        bool flipicon ()
        void set_flipicon (bool value)
        void set_background (string name)
        void set_icon (string name)


    class ufo.uiCheckBox: uiNode
        void set_background (string name)
        void set_iconchecked (string name)
        void set_iconunchecked (string name)
        void set_iconunknown (string name)


    class ufo.uiConFunc: uiNode


    class ufo.uiContainer: uiNode
        int selectedid ()
        LUA_EVENT on_select ()


    class ufo.uiBaseInventory: uiContainer
        int filtertype ()
        int columns ()
        bool is_displayweapon ()
        bool is_displayweaponammo ()
        bool is_displayammo ()
        bool is_displayimplant ()
        bool is_displayunavailable ()
        bool is_displayunavailableammo ()
        bool is_displayavailableontop ()
        void set_displayweapon (bool value)
        void set_displayweaponammo (bool value)
        void set_displayammo (bool value)
        void set_displayimplant (bool value)
        void set_displayunavailable (bool value)
        void set_displayunavailableammo (bool value)
        void set_displayavailableontop (bool value)
        int viewpos ()
        int viewsize ()
        int fullsize ()
        void set_viewpos (int pos)
        void set_viewsize (int size)
        void set_fullsize (int size)
        LUA_EVENT on_viewchange ()


    class ufo.uiData: uiNode
        char as_string ()
        int as_integer ()
        float as_float ()
        void set_value (string value)
        void set_value (int value)
        void set_valuef (float value)


    class ufo.uiGeoscape: uiNode
        void zoomin ()
        void zoomout ()


    class ufo.uiImage: uiNode
        bool is_keepratio ()
        bool is_mousefx ()
        vec2_struct_t texh ()
        vec2_struct_t texl ()
        void set_keepratio (bool value)
        void set_mousefx (bool value)
        void set_source (string name)
        void set_texh (float v1, float v2)
        void set_texl (float v1, float v2)


    class ufo.uiEkg: uiImage
        float scrollspeed ()
        float cvarscale ()
        void set_scrollspeed (float value)
        void set_cvarscale (float value)


    class ufo.uiLineChart: uiNode
        bool is_showaxes ()
        int dataid ()
        void set_dataid (string name)
        void set_showaxes (bool value)
        void set_axescolor (float r, float g, float b, float a)


    class ufo.uiMessageList: uiAbstractScrollableNode


    class ufo.uiModel: uiNode
        bool is_autoscale ()
        bool is_mouserotate ()
        vec3_struct_t angles ()
        vec3_struct_t origin ()
        vec3_struct_t omega ()
        vec3_struct_t scale ()
        char model ()
        char skin ()
        char animation ()
        char tag ()
        void set_autoscale (bool value)
        void set_mouserotate (bool value)
        void set_angles (float a1, float a2, float a3)
        void set_origin (float a1, float a2, float a3)
        void set_omega (float a1, float a2, float a3)
        void set_scale (float a1, float a2, float a3)
        void set_model (string name)
        void set_skin (string name)
        void set_animation (string name)
        void set_tag (string name)


    class ufo.uiItem: uiModel
        bool is_containerlike ()
        void set_containerlike (bool value)


    class ufo.uiOption: uiNode
        bool is_collapsed ()
        bool is_flipicion ()
        bool is_truncated ()
        char label ()
        char value ()
        int count ()
        void set_label (string text)
        void set_value (string text)
        void set_collapsed (bool value)
        void set_flipicion (bool value)
        void set_truncated (bool value)
        void set_icon (string name)


    class ufo.uiOptionList: uiAbstractOptionNode


    class ufo.uiOptionTree: uiAbstractOptionNode
        void set_selectedvalue (string value)


    class ufo.uiPanel: uiAbstractScrollableNode
        bool is_wheelscrollable ()
        int layout ()
        int layoutmargin ()
        int layoutcolumns ()
        void set_layout (int value)
        void set_layoutmargin (int value)
        void set_layoutcolumns (int value)
        void set_wheelscrollable (bool value)
        void set_background (string name)


    class ufo.uiRadar: uiNode


    class ufo.uiRadioButton: uiNode
        bool is_flipicon ()
        char as_string ()
        float as_float ()
        void set_value (string value)
        void set_value (float value)
        void set_flipicon (bool value)
        void set_background (string name)
        void set_icon (string name)


    class ufo.uiRows: uiNode
        int current ()
        int lineheight ()
        void set_current (int value)
        void set_lineheight (int value)


    class ufo.uiSelectBox: uiNode


    class ufo.uiSequence: uiNode
        bool is_playing ()
        void set_source (string name)
        LUA_EVENT lua_onEnd ()


    class ufo.uiSpinner: uiAbstractValueNode
        bool is_horizontal ()
        bool is_inverted ()
        int mode ()
        void set_background (string name)
        void set_topicon (string name)
        void set_bottomicon (string name)
        void set_mode (int mode)
        void set_horizontal (bool value)
        void set_inverted (bool value)


    class ufo.uiString: uiNode
        int longlines ()
        void set_longlines (int value)


    class ufo.uiTab: uiAbstractOptionNode


    class ufo.uiTBar: uiAbstractValueNode
        vec2_struct_t texh ()
        vec2_struct_t texl ()
        void set_source (string name)
        void set_texh (float v1, float v2)
        void set_texl (float v1, float v2)


    class ufo.uiText: uiAbstractScrollableNode
        int dataid ()
        int lineheight ()
        int lineselected ()
        int longlines ()
        char textselected ()
        int tabwidth ()
        void set_dataid (int id)
        void set_longlines (int value)
        void set_lineheight (int value)
        void set_lineselected (int line)
        void set_tabwidth (int value)


    class ufo.uiText2: uiText


    class ufo.uiTextEntry: uiNode
        bool is_password ()
        bool is_clickoutabort ()
        int cursorposition ()
        void set_password (bool value)
        void set_clickoutabort (bool value)
        void set_background (string name)
        LUA_EVENT on_textabort ()


    class ufo.uiTextList: uiText


    class ufo.uiTexture: uiNode
        void set_source (string name)


    class ufo.uiTimer: uiNode
        int timeout ()
        void set_timeout (int value)
        LUA_EVENT lua_onEvent ()


    class ufo.uiVideo: uiNode
        bool is_nosound ()
        void set_nosound (bool value)
        void set_source (string name)
        LUA_EVENT lua_onEnd ()


    class ufo.uiVScrollbar: uiAbstractScrollbarNode


    class ufo.uiWidget: uiImage


    class ufo.uiWindow: uiNode
        bool is_fullscreen ()
        bool is_modal ()
        void close ()
        void open ()
        void set_background (string name)
        void set_fullscreen (bool value)
        void set_modal (bool value)
        void set_fill (bool value)
        void set_dragbutton (bool value)
        void set_closebutton (bool value)
        LUA_EVENT on_windowopened ()
        LUA_EVENT on_windowclosed ()


    class ufo.uiZone: uiNode
        bool is_repeat ()
        int clickdelay ()
        void set_repeat (bool value)
        void set_clickdelay (int value)

## global constants

    constants (from enum uiDataIDs_t):

    ufo.TEXT_NULL
    ufo.TEXT_STANDARD
    ufo.TEXT_LIST
    ufo.TEXT_LIST2
    ufo.TEXT_UFOPEDIA
    ufo.TEXT_UFOPEDIA_REQUIREMENT
    ufo.TEXT_BUILDINGS
    ufo.TEXT_BUILDING_INFO
    ufo.TEXT_RESEARCH
    ufo.TEXT_POPUP
    ufo.TEXT_POPUP_INFO
    ufo.TEXT_AIRCRAFT_LIST
    ufo.TEXT_AIRCRAFT_INFO
    ufo.TEXT_MULTISELECTION
    ufo.TEXT_PRODUCTION_LIST
    ufo.TEXT_PRODUCTION_AMOUNT
    ufo.TEXT_PRODUCTION_INFO
    ufo.TEXT_EMPLOYEE
    ufo.TEXT_MOUSECURSOR_RIGHT
    ufo.TEXT_PRODUCTION_QUEUED
    ufo.TEXT_STATS_MISSION
    ufo.TEXT_STATS_BASES
    ufo.TEXT_STATS_NATIONS
    ufo.TEXT_STATS_EMPLOYEES
    ufo.TEXT_STATS_COSTS
    ufo.TEXT_STATS_INSTALLATIONS
    ufo.TEXT_STATS_7
    ufo.TEXT_BASE_LIST
    ufo.TEXT_BASE_INFO
    ufo.TEXT_TRANSFER_LIST
    ufo.TEXT_TRANSFER_LIST_AMOUNT
    ufo.TEXT_TRANSFER_LIST_TRANSFERED
    ufo.TEXT_MOUSECURSOR_PLAYERNAMES
    ufo.TEXT_CARGO_LIST
    ufo.TEXT_CARGO_LIST_AMOUNT
    ufo.TEXT_UFOPEDIA_MAILHEADER
    ufo.TEXT_UFOPEDIA_MAIL
    ufo.TEXT_MARKET_NAMES
    ufo.TEXT_MARKET_STORAGE
    ufo.TEXT_MARKET_MARKET
    ufo.TEXT_MARKET_PRICES
    ufo.TEXT_CHAT_WINDOW
    ufo.TEXT_AIREQUIP_1
    ufo.TEXT_AIREQUIP_2
    ufo.TEXT_BASEDEFENCE_LIST
    ufo.TEXT_TIPOFTHEDAY
    ufo.TEXT_GENERIC
    ufo.TEXT_XVI
    ufo.TEXT_MOUSECURSOR_TOP
    ufo.TEXT_MOUSECURSOR_BOTTOM
    ufo.TEXT_MOUSECURSOR_LEFT
    ufo.TEXT_MESSAGEOPTIONS
    ufo.TEXT_UFORECOVERY_NATIONS
    ufo.TEXT_UFORECOVERY_UFOYARDS
    ufo.TEXT_UFORECOVERY_CAPACITIES
    ufo.TEXT_MATERIAL_STAGES
    ufo.TEXT_IRCCONTENT
    ufo.TEXT_IRCUSERS
    ufo.TEXT_MULTIPLAYER_USERLIST
    ufo.TEXT_MULTIPLAYER_USERTEAM
    ufo.TEXT_ITEMDESCRIPTION
    ufo.TEXT_MISSIONBRIEFING
    ufo.TEXT_MISSIONBRIEFING_TITLE
    ufo.TEXT_MISSIONBRIEFING_VICTORY_CONDITIONS
    ufo.OPTION_LANGUAGES
    ufo.OPTION_JOYSTICKS
    ufo.OPTION_VIDEO_RESOLUTIONS
    ufo.OPTION_SINGLEPLAYER_SKINS
    ufo.OPTION_MULTIPLAYER_SKINS
    ufo.OPTION_UFOPEDIA
    ufo.OPTION_UFOS
    ufo.OPTION_DROPSHIPS
    ufo.OPTION_BASELIST
    ufo.OPTION_TEAMDEFS
    ufo.OPTION_PRODUCTION_REQUIREMENTS
    ufo.OPTION_CAMPAIGN_LIST
    ufo.LINESTRIP_FUNDING
    ufo.LINESTRIP_COLOR
    ufo.UI_MAX_DATAID

    constants (from enum longlines_t):

    ufo.LONGLINES_WRAP
    ufo.LONGLINES_CHOP
    ufo.LONGLINES_PRETTYCHOP
    ufo.LONGLINES_LAST

    constants (from enum align_t):

    ufo.ALIGN_UL
    ufo.ALIGN_UC
    ufo.ALIGN_UR
    ufo.ALIGN_CL
    ufo.ALIGN_CC
    ufo.ALIGN_CR
    ufo.ALIGN_LL
    ufo.ALIGN_LC
    ufo.ALIGN_LR
    ufo.ALIGN_UL_RSL
    ufo.ALIGN_UC_RSL
    ufo.ALIGN_UR_RSL
    ufo.ALIGN_CL_RSL
    ufo.ALIGN_CC_RSL
    ufo.ALIGN_CR_RSL
    ufo.ALIGN_LL_RSL
    ufo.ALIGN_LC_RSL
    ufo.ALIGN_LR_RSL

    constants (from enum layoutAlign_t):

    ufo.LAYOUTALIGN_NONE
    ufo.LAYOUTALIGN_H_MASK
    ufo.LAYOUTALIGN_H_LEFT
    ufo.LAYOUTALIGN_H_MIDDLE
    ufo.LAYOUTALIGN_H_RIGHT
    ufo.LAYOUTALIGN_V_MASK
    ufo.LAYOUTALIGN_V_TOP
    ufo.LAYOUTALIGN_V_MIDDLE
    ufo.LAYOUTALIGN_V_BOTTOM
    ufo.LAYOUTALIGN_TOPLEFT
    ufo.LAYOUTALIGN_TOP
    ufo.LAYOUTALIGN_TOPRIGHT
    ufo.LAYOUTALIGN_LEFT
    ufo.LAYOUTALIGN_MIDDLE
    ufo.LAYOUTALIGN_RIGHT
    ufo.LAYOUTALIGN_BOTTOMLEFT
    ufo.LAYOUTALIGN_BOTTOM
    ufo.LAYOUTALIGN_BOTTOMRIGHT
    ufo.LAYOUTALIGN_SPECIAL
    ufo.LAYOUTALIGN_FILL
    ufo.LAYOUTALIGN_MAX
    ufo.LAYOUTALIGN_ENSURE_32BIT

    constants (from enum panelLayout_t):

    ufo.LAYOUT_NONE
    ufo.LAYOUT_TOP_DOWN_FLOW
    ufo.LAYOUT_LEFT_RIGHT_FLOW
    ufo.LAYOUT_BORDER
    ufo.LAYOUT_PACK
    ufo.LAYOUT_STAR
    ufo.LAYOUT_CLIENT
    ufo.LAYOUT_COLUMN
    ufo.LAYOUT_MAX
    ufo.LAYOUT_ENSURE_32BIT

    constants (from enum itemFilterTypes_t):

    ufo.FILTER_S_PRIMARY
    ufo.FILTER_S_SECONDARY
    ufo.FILTER_S_HEAVY
    ufo.FILTER_S_MISC
    ufo.FILTER_S_ARMOUR
    ufo.FILTER_S_IMPLANT
    ufo.MAX_SOLDIER_FILTERTYPES
    ufo.FILTER_CRAFTITEM
    ufo.FILTER_UGVITEM
    ufo.FILTER_AIRCRAFT
    ufo.FILTER_DUMMY
    ufo.FILTER_DISASSEMBLY
    ufo.MAX_FILTERTYPES
    ufo.FILTER_ENSURE_32BIT