---
id: HZ7peROiNf64DG2YyxZxN
title: Monitoring Uwsgi Workers   like Htop
desc: ''
updated: 1642640076188
created: 1642639963415
---
workon pine

property author : "Roman"
property pine : {"pine1", "pine2", "pine3", "pine4", "pine5", "pine6", "pine7", "pine8", "pine9", "pine10"}
-- property pine : {"oak1", "oak2", "oak3", "oak4", "oak5", "oak6", "oak7", "oak8", "oak9", "oak10"}
on splitH(ses, title)
    local new_ses
    tell application "iTerm"
        set new_ses to split horizontally with same profile ses command "~/.bin/sshenv pine " & title & " \"~/.virtualenvs/pine/bin/uwsgitop-easy\""
        set name of new_ses to title
    end tell
    return new_ses
end splitH
on run
    local desktop_bounds, my_ses
    tell application "Finder"
        set desktop_bounds to bounds of window of desktop
    end tell
    
    tell application "iTerm"
        set my_window to create window with default profile command "~/.bin/sshenv pine " & (item 1 of pine) & " \"~/.virtualenvs/pine/bin/uwsgitop-easy\""
        set bounds of my_window to desktop_bounds
        set my_ses to {first session of first tab of my_window}
    end tell
    
    repeat with i from 2 to (length of pine)
        set my_ses to my_ses & {splitH(item (i - 1) of my_ses, item i of pine)}
    end repeat
end run
on a_duck()
    tell application "iTerm"
        delay 2
        repeat with sess in my_ses
            repeat while is processing of sess is true
                delay 0.5
            end repeat
            repeat while ((paragraph -2 of (text of sess)) does not contain "$")
                delay 0.3
            end repeat
            
            if (paragraph -2 of (text of sess)) does not contain "pine" then
                exit repeat
                write sess text "workon pine"
            end if
        end repeat
    end tell
    --(text of ses_23)
end a_duck
