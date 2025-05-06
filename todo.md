    Term2 3.5.13#!/bin/zsh
SESSION_NAME="zeus"

make_new_tmux_session() {
    tmux new-session -s $SESSION_NAME
    tmux split-window -h -t $SESSION_NAME:0

    tmux split-window -v -t $SESSION_NAME:0.1
    tmux split-window -h -t $SESSION_NAME:0.1
    tmux split-window -h -t $SESSION_NAME:0.3
    # extra panel to get rid of garbage chars
    tmux split-window -v -t $SESSION_NAME:0.4
    tmux resize-pane -t "$SESSION_NAME":0.1 -L $(tmux display-message -p -t "$SESSION_NAME":0.2 '#{pane_width}')
    tmux send-keys -t $SESSION_NAME:0.1 "htop" C-m
    tmux send-keys -t $SESSION_NAME:0.2 "y" C-m
    tmux send-keys -t $SESSION_NAME:0.4 "cd ${TODO_DIR} && vim todo.md" C-m
    #getting rid of garbage panel
    tmux send-keys -t $SESSION_NAME:0.5 "clear" C-m

}

if [ ! "$TMUX" ]; then
    ⦙   tmux attach -t $SESSION_NAME || make_new_tmux_session
fi- [ ] task 2
- [ ] task 3
- [ ] task5
