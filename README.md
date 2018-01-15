# timestamp

## bash
    # export PS1="* [\d \t][\$(date +%a)][\s] $PS1 "
    export PS1="* [\$(date +%F) \t][\$(date +%a)][\s] $PS1 "
## console
    # sudo apt install picocom
    sudo picocom -b 115200 /dev/ttyUSB0 | ts '[%F %T][<device><f.w. ver.>]' | tee -a "$(date +%F)-$(($(ls | grep "$(date +%F)-" | wc -l)+1))"-"$(ps -o pid,tty | grep $$ | awk -F ' |/' '{print $(NF-1) $NF}')"--<device>-<f.w. ver.>.txt
## vim
    " timestamp
    nmap <F3> i<C-R>=strftime("[%F %T][%a] ")<CR>
    imap <F3> <C-R>=strftime("[%F %T][%a] ")<CR>
