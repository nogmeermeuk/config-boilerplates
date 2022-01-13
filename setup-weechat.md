# Setup WeeChat

This setup should work for [WeeChat >= 2.8](https://weechat.org/doc/).

## Secure some shizzle

### Set secure data

```
/secure passphrase <super secret passphrase>
/secure set blinkenshell_nickserv_password <NickServ Password>
/secure set darkscience_nickserv_password <NickServ Password>
/secure set liberachat_nickserv_password <NickServ Password>
/secure set tildechat_nickserv_password <NickServ Password>
/save
```

### Disable CTCP replies

```
/set irc.ctcp.action ""
/set irc.ctcp.clientinfo ""
/set irc.ctcp.finger ""
/set irc.ctcp.ping ""
/set irc.ctcp.source ""
/set irc.ctcp.time ""
/set irc.ctcp.userinfo ""
/set irc.ctcp.version ""
/save
```

## Networks

### Set default server settings

```
/set irc.server_default.command_delay 5
/set irc.server_default.msg_part ""
/set irc.server_default.msg_quit ""
/set irc.server_default.nicks "meuk"
/set irc.server_default.ssl on
/save
```

### Add Blinkenshell

```
/server add blinkenshell irc.blinkenshell.org/6697
/set irc.server.blinkenshell.autoconnect on
/set irc.server.blinkenshell.sasl_password "${sec.data.blinkenshell_nickserv_password}"
/set irc.server.blinkenshell.sasl_username "meuk"
/save
```

### Add Dark Science

```
/server add darkscience irc.darkscience.net/6697
/set irc.server.darkscience.autoconnect on
/set irc.server.darkscience.autojoin "#darkscience,#movies"
/set irc.server.darkscience.sasl_password "${sec.data.darkscience_nickserv_password}"
/set irc.server.darkscience.sasl_username "meuk"
/save
```

### Add Libera.Chat

```
/server add liberachat irc.libera.chat/6697
/set irc.server.liberachat.autoconnect on
/set irc.server.liberachat.autojoin "#tilde.team"
/set irc.server.liberachat.sasl_password "${sec.data.liberachat_nickserv_password}"
/set irc.server.liberachat.sasl_username "meuk"
/save
```

### Add tilde.chat

```
/server add tildechat irc.tilde.chat/6697
/set irc.server.tildechat.autoconnect on
/set irc.server.tildechat.autojoin "#institute,#meta"
/set irc.server.tildechat.sasl_password "${sec.data.tildechat_nickserv_password}"
/set irc.server.tildechat.sasl_username "meuk"
/save
```

## Plugins

### Disable unused plugins

Check which plugins are loaded on startup with `/plugin` and adjust the following command according to your needs:

```
/set weechat.plugin.autoload "*,!perl,!relay,!ruby,!spell,!xfer"
/save
```

### Configure logger

```
/set logger.file.flush_delay 5
/set logger.file.nick_prefix "["
/set logger.file.nick_suffix "]"
/set logger.mask.irc "%Y/$server/$channel.weechatlog"
/save
```

## Scripts

### Install scripts

```
/script install autosort.py go.py urlgrab.py
```

### Configure urlgrab.py

It's lame but `%h/logs/urlgrab_urls.log` doesn't work...

```
/set urlgrab.default.historysize 999
/set urlgrab.default.time_format "%Y-%m-%d %H:%M:%S"
/set urlgrab.default.url_log "~/.weechat/logs/urlgrab_urls.log"
/save
```

## Look & Feel

### Buflist

```
/set irc.look.server_buffer independent
/set buflist.format.number "${number}${if:${number_displayed}?. : }"
/save
```

### Prettify some shizzle

```
/set weechat.look.bar_more_down "▼▼"
/set weechat.look.bar_more_left "◀◀"
/set weechat.look.bar_more_right "▶▶"
/set weechat.look.bar_more_up "▲▲"
/set weechat.look.prefix_action "=*="
/set weechat.look.prefix_error "=!="
/set weechat.look.prefix_network "=i="
/set weechat.look.prefix_same_nick "⤷"
/set weechat.look.separator_horizontal "—"
/save
```

### Colors

```
/set buflist.format.buffer "${format_number}${indent}${format_nick_prefix}${if:${current_buffer}?${color:darkgray,32}:${color_hotlist}}${format_name}"
/set buflist.format.buffer_current "${color:darkgray,32}${format_buffer}"
/set buflist.format.hotlist_highlight "${color:200}"
/set buflist.format.hotlist_private "${color:200}"
/set irc.look.color_nicks_in_nicklist on
/set weechat.bar.status.color_bg 0
/set weechat.bar.title.color_bg 0
/set weechat.color.chat_nick_colors "1,2,3,4,6,7,9,10,11,12,13,14,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,182,183,184,244,225,226,227"
/save
```

## Some miscellaneous options

```
/set irc.look.smart_filter on
/filter add irc_smart * irc_smart_filter *
/set irc.look.smart_filter_delay 1
/set weechat.bar.nicklist.size 20
/set weechat.bar.nicklist.size_max 20
/set weechat.look.prefix_align_max 10
/save
```
