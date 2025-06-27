# read_line_installation_script
*For MiniShell Project In Macs*
**Must Heve Brew Installed**

## Make File Section:
```Makefile

#Ssystem detection
UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Darwin)
	READLINE_DIR := $(shell brew --prefix readline)
CFLAGS       = -Wall -Wextra -Werror -fsanitize=address -I$(INCLUDE_DIR) -I$(READLINE_DIR)/include

	LDFLAGS      = -L$(READLINE_DIR)/lib -lreadline 
	os_msg = "$(GREEN)OS DETECTED Mac!$(RESET)"

else ifeq ($(UNAME_S),Linux)
CFLAGS       = -Wall -Wextra -Werror -Wunreachable-code


	LDFLAGS      = -L$(READLINE_DIR)/lib -lreadline -lhistory -lncurses
	os_msg = "$(GREEN)OS DETECTED Linux!$(RESET)"
endif


```

## MANUAL INSTALL:

need to install readline from brew
```
brew install readline
```

install ncures using brew 
```
brew install ncurses
```

**Link `readline`**:
```
brew link readline --force
```

add this is the makefile
```
LDFLAGS = "-L$(brew --prefix readline)/lib"
CFLAGS = -Wall -Wextra -Werror -Wunreachable-code I$(READLINE_DIR)/include
```

may need to do this as well 
```
export LDFLAGS="-L$(brew --prefix readline)/lib"
export CPPFLAGS="-I$(brew --prefix readline)/include"
```
