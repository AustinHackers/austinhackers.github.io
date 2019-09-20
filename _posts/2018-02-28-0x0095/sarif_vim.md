# Plugins for an awesome vim setup

1. Install gruvbox for vs code like syntax highlighting
1. Install youcompleteme for auto complete

# Vimrc tweaks
```
syntax on
set number "enable line numbers
```
### Gruvbox settings:
```
let g:gruvbox_contrast_dark = 'hard'
colorscheme gruvbox
set background=dark
```
```
" tab vs spaces flamewar
set tabstop=4
set shiftwidth=4
set expandtab
```

# Handy commands to fully replace VS Code
## tabs
- ```:tabe filename```
    - opens new tabe with filename
- ```gt```
    - swtich tabs
- ```:vsplit (or vsp) filename```
    - opens a verticle split tab like thing
    - to switch between verticle splits use ```Ctrl-w Ctrl-w```
## fancy unlreated shortcuts
- ```.```
    - repeats last edit
- ```g;```
    - goto last edit
- ```ciw```
    - replaces current word under cursosr
- ```gg=G```
    - format your code. **Do not use for python**
- ```:terminal```
    - opens a terminal inside of vim