# shell-2-alex-lin64-pauljeong333
alex-lin64-pauljeong333 team's shell-2 repo

shell 2 - Alex Lin, Paul Jeong


    structure of shell 2:
        
        the shell is split into the main repl look in sh.c and all the support 
        functions in common.c, parse.c, and check_error.c.  the main repl in 
        sh.c first intializes necessary data structures to store the command 
        line input.  the first support function called in parse(), within 
        parse.c, which parses through the raw command line input and produces 
        the tokens and the argv array.  further, parse_redir() parses the 
        redirections and is error check with parse_redir_err(), within the 
        check_error.c file.  a function parse_fg_bg() is called next to parse
        the command for any occurences of bg and fg, so that the fg and bg 
        commands run properly (or detect any errors). next, run_command() is 
        called to detect built-in, including fg and bg, commands, and this is 
        error checked with the return value of run_command().  specifically, for
        fg and bg, run command will call run_fg() or run_bg() based on whether 
        command parsed is "fg" or "bg". if no built-in's are called or any error 
        is discovered, the repl forks a child process, where redirections 
        are dealt with, the signals are set to default behavior, and then the 
        command is executed.  after returning form the child, update_cur_job()
        and update_bg_job() (part of print_prompt_update()) are called to 
        properly update the jobs list and print out any lines about processes
        running/stopped. other support functions include syscall_err(), 
        with error checks syscalls, perror to error check, and 
        printprompt_err() and printf_err(), which error checks printf and 
        printing the prompt. 

    bugs:

        there are no known bugs at the momment.

    extra features:

        there were no extra features implemented.

    how to compile:

        to compile, cd into the shell2 directory.  

        to compile the shell with prompts, run the command

            make 33sh

        to compile the shell w/o prompts, run the command

            make 33noprompt
        
        to compile both 33sh and 33noprompt, run

            make all
        
        to remove all compilations, run

            make clean

        to run either 33sh or 33noprompt
        
            ./33sh  
            ./33noprompt
        
        type exit or CTRL-\ to quit the shell

    distribution of work:

        the work was evenly distributed between Alex and Paul.  most of the work 
        was completed together, with one partner typing and the other helping 
        with design and looking for bugs, coming up with solutions, etc. we used
        pair programming.

       
