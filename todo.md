        Term2 3.5.13tmux split-window -v -t $SESSION_NAME:0.1 -c "${TODO_DIR}" "vim todo.md"Term2 3.5.13make_new_tmux_session() {
    tmux new-session -s $SESSION_NAME -d
    tmux split-window -h -t $SESSION_NAME
    tmux split-window -v -t $SESSION_NAME

    # Launch vim in bottom-right pane
    tmux send-keys -t $SESSION_NAME:0.2 "vim ${TODO_DIR}/todo.md" C-m

    # Wait to ensure Vim has fully initialized
    sleep 1

    # Send 'y' to another pane (top-right)
    tmux send-keys -t $SESSION_NAME:0.1 "y" C-m

    tmux attach-session -t $SESSION_NAME
}
= TODOS =
- [ ] task 1
- [ ] task 2
