FROM ubuntu:20.04

RUN apt update -y
RUN apt upgrade -y
RUN apt install curl -y
RUN apt install git -y

RUN curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs
RUN npm config set ignore-scripts false

RUN apt install zsh -y

RUN sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

#installing spaceship
RUN npm install -g spaceship-prompt
RUN echo "SPACESHIP_PROMPT_ORDER=(\nuser          # Username section\ndir           # Current directory section\nhost          # Hostname section\ngit           # Git section (git_branch + git_status)\nhg            # Mercurial section (hg_branch  + hg_status)\nexec_time     # Execution time\nline_sep      # Line break\nvi_mode       # Vi-mode indicator\njobs          # Background jobs indicator\nexit_code     # Exit code section\nchar          # Prompt character\n)\nSPACESHIP_USER_SHOW=always\nSPACESHIP_PROMPT_ADD_NEWLINE=false\nSPACESHIP_CHAR_SYMBOL=\"❯\"\nSPACESHIP_CHAR_SUFFIX=\" \"" >> /root/.zshrc

# Installing font
WORKDIR /root/.fonts
RUN git clone https://github.com/JetBrains/JetBrainsMono.git

# Installing zinit and plugins
RUN sh -c "$(curl -fsSL https://git.io/zinit-install)"
RUN echo "zinit light zdharma/fast-syntax-highlighting\nzinit light zsh-users/zsh-autosuggestions\nzinit light zsh-users/zsh-completions" >> /root/.zshrc

# Installing k6
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
RUN echo "deb https://dl.k6.io/deb stable main" | tee /etc/apt/sources.list.d/k6.list
RUN apt-get update
RUN apt-get install k6 -y


CMD ["zsh"]