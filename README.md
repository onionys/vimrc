# Normal Mode

進入 insert mode。`i`: 當前位置。`a`: 下一個字。`I`: 行首。`A`: 行尾。`o`:新增下一行。`O`:新增上一行。`R`: 取代模式

### 移動游標 

`hjkl`: 上下左右。`w`:下一個字首。`b`:上一個字首。`e`:下一個字尾

蒐尋字間移動。`*`:下一個找到的字。`#`:上一個找到的字。

行移動。`^`: 移到行首。`$`:移到行尾。`20G`: 移到指定行數20。`''` : 移到上一個行數。

畫面移動:`<ctrl> + f`: 向下移動一個畫面 。`<ctrl> + b`: 向上移動一個畫面。`gg`: 移動到檔案開頭。`G`: 移動到檔案結尾。

### 編輯指令

剪下。`x`: 剪下游標所在的字元。`dd`: 剪下當前行的內容。`d3d`: 剪下三行的內容。

貼上。`p`: 貼在游標之後。`P`: 貼在游標之前。

複製。`yw`: 複製所在的單字。`yy`: 複製當前行內容。`y3y`:複製從當前行開始向下總共三行內容。

取代。`r`: 取代游標所在的字元

Undo and Redo: `u` and `<ctrl> + r`

### 動作巨集

`qa`:開始錄製模式。`q` : 錄製模式下離開錄製棤式。`@a`:執行錄製好的動作

### 分割視窗

使用 Command Line Mode 分割視窗。`:sp`: 上下分割。 `:vsp` : 左右分割

**在不同的分割視窗移動**

`<ctrl> + w` then `<ctrl> + 上` : 游標移到上面的分割視窗

`<ctrl> + w` then `<ctrl> + j`  : 游標移到上面的分割視窗

其他方向比照辦理。

**視窗大小調整**

`<ctrl> + w` then `<` : 縮小寬度

`<ctrl> + w` then `>` : 增加寬度

`<ctrl> + w` then `+` : 縮小高度

`<ctrl> + w` then `-` : 增加高度

可以在指令前先加數目:

`10` then `<ctrl> + w` then `<`

# Command Line Mode

行範圍指定剪下。`:10,20d`: 將第10行到第20行的內容剪下。

檔案操作。`:w`:存檔。`w!`:強制存檔。`:e <filename>`:開啟指定檔案。`:q`:離開vim。`:wq`:存檔後離開vim。

尋找指定字串(ex:`hello`)。`:/hello`:尋找字。`/\chello`:尋找字(`\c`表示無視大小寫)。`n`:下一個。`N`:上一個。

### 尋找 and Replace:

下面的例子都為找到 `hello` 並取代為 `world`。

`:s/hello/world/g`:所在行的取代。`%s/hello/world/g`:全部取代。`%s/hello/world/gc`:全部取代，取代前詢問

`:1,20s/hello/world/g`:指定行數取代(1~20行)

### 環境設定 (可寫在 home 目錄底下的 `.vimrc` 之後自動生效)

`:set nu`:顯示行號。`:set nonu`:不顯示行號。`:set hlsearch`:找到的字用高亮度顯示。

自動縮排設定

    :set autoindent
	:set smartindent
	:set tabstop=4
	:set shiftwidth=4
	:set expandtab

`:set background=dark` : 設定背景為 dark

**Insert Mode Key Mapping Set**

	:imap hello<tab> HelloWorld.
	:imap dth<tab> dscan th -.2 .2 20 1<CR>

`imap` 表示 Insert Mode Key Mapping，`<tab>`為 Tab 鍵，`<CR>` 為換行，`<esc>`為 ESC 鍵。

寫在 `.vimrc` 裡的話，下面為指定副檔名(`.do`)才會生效的寫法

	autocmd BufRead *.do imap dth<tab> dscan th -.2 .2 20 1<CR>

其他的模式也可以設定 key mapping。

	vmap 為 virual mode
	cmap 為 command line mode
	nmap 為 normal mode

# Insert Mode

`<ESC>`:回到 Normal Mode

自動拼字。`<ctrl> + n` : 當前檔案內容為 base。`<ctrl> + x` `<ctrl> + f` : 當前資料夾下檔名為 base。

