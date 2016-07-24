Vundle, a plug-in manager for Vim.
Vundle, 一个管理Vim插件的插件.

1. ABOUT VUNDLE
    Vundle is short for Vim bundle and is a Vim plugin manager.
    Vundle 是Vim bundle 的精简版本，同样也是一个Vim 插件管理插件

    - keep track of and configure your scripts right in the `.vimrc`
    正确的跟踪和配置在 `.vimrc` 中的脚本

    - install configured scripts (a.k.a. bundle)
    安装配置好的脚本

    - update configured scripts
    更新配置好的脚本

    - search by name all available Vim scripts
    允许在Vim的脚本中通过名字搜索插件

    - clean unused scripts up
    清楚无用的脚本

    - run the above actions in a single keypress with interactive mode
    在vim中的交互模式下，通过一个按键运行以上的功能

    Vundle automatically ...
    Vundle 自动化...

    - manages the runtime path of your installed scripts
    管理你所安装的脚本的运行时路径

    - regenerates help tags after installing and updating
    在安装和更新之后重新。。帮助标签

    Vundle’s search uses http://vim-scripts.org to provide a list of all available Vim scripts
    vundle 的搜索功能使用org组织提供的一系列可用的vim脚本

    Vundle is undergoing an interface change, see |vundle-interface-change| for more information
    vundle的接口正在改变，可以看看|vundle-interface-change|获取更详细的信息


2. QUICK START
    - Introduction：
    - 介绍：

    Installation requires `Git` and triggers git clone for each configured repository to `~/.vim/bundle/` by default. Curl is required for search.
    安装需要  `Git` 并且通过 git clone 去trigger每一个配置好的repo 默认的trgger到 `~/.vim/bundle/`中，搜索需要安装 `Curl`

    If you run into any issues, please consult the FAQ at https://github.com/VundleVim/Vundle.vim/wiki
    如果遇到了任何的问题，请先到wiki中的FAQ中去寻找答案

    - Setup Vundle:
    - 开始使用 Vundle:

    git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

    - Configure bundles:
    - 配置 bundles:

    Put this at the top of your `.vimrc` to use Vundle. Remove bundles you don't need, they are for illustration purposes.
    使用 Vundle，就将这个放在你的 `.vimrc` 的上面。删除你不需要的bundles，这些都是是用于例证的。

        ```
        set nocompatible                      " be iMproved,required 用于改善，需要
        filetype off                          " required 需要

        " set the runtime path to include Vundle and initialize
        "在运行时路径中加入Vundle，然后初始化vundle
        set rtp+=~/.vim/bundle/Vundle.vim
        call vundle#begin()

        " alternatively, pass a path where Vundle should install plugins
        " 或者，将vundle 所装插件的路径传进去
        "call vundle#begin('~/some/path/here')

        " let Vundle manage Vundle, required
        " 让 Vundle 管理 Vundle。把Vundle作为插件管理起来
        Plugin 'VundleVim/Vundle.vim'

        " The following are examples of different formats supported.
        " 以下是一些栗子，向你展示所支持的不同的格式
        " Keep Plugin commands between vundle#begin/end.
        " 保证插件命令在 vundle#begin/end 之间

        " plugin on GitHub repo
        " 插件在github的repo上
        Plugin 'tpope/vim-fugitive'

        " plugin from http://vim-scripts.org/vim/scripts.html
        " 插件在github的repo上
        Plugin 'L9'

        " Git plugin not hosted on GitHub
        " git 插件咩有在github的repo上
        Plugin 'git://git.wincent.com/command-t.git'

        " git repos on your local machine (i.e. when working on your own plugin)
        " git 的 repo 在你的本地机器上（比如说，你自己写了一个插件）
        Plugin 'file:///home/gmarik/path/to/plugin'

        " The sparkup vim script is in a subdirectory of this repo called vim.
        " 如果 sparkup vim 脚本在这个repo的子目录下面，并且叫做vim
        " Pass the path to set the runtimepath properly.
        " 将路径穿进去，并且设置 runtimepath 属性
        Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}

        " Avoid a name conflict with L9
        " 避免名字和 L9 冲突
        Plugin 'user/L9', {'name': 'newL9'}

        " All of your Plugins must be added before the following line
        " 你所有的插件都必须添加在在下面这行代码的上面
        call vundle#end()                   " required  需要
        filetype plugin indent on           " required

        " To ignore plugin indent changes, instead use:
        " 忽略插件缩进的改变，使用:
        "filetype plugin on
        "
        " Brief help
        " :PluginList - list configured plugins - 列出所有配置的插件
        " :PluginInstall(!) - install (update) plugins －install 或者 update 插件
        " :PluginSearch(!) foo - search (or refresh cache first) for foo － 搜索
        " :PluginClean(!) - confirm (or auto-approve) removal of unused plugins － 删除不用的插件
        "
        " see :h vundle for more details or wiki for FAQ
        " Put your non-Plugin stuff after this line
        ```

    - Install configured bundles:
    - 安装配置 bundles:

    Launch vim and run  " 启动vim,然后运行
    :PluginInstall

    To install from command line   " 通过命令行安装
    vim +PluginInstall +qall

3.PLUGINS

    - CONFIGURING PLUGINS
    Vundle tracks what plugins you want configured by the `Plugin` commands in your `.vimrc`. Each `Plugin` command tells Vundle to activate the script on startup adding it to your |runtimepath|. Commenting out or removing the line will disable the `Plugin`.
    vundle 跟踪你想要在你的 .vimrc 文件中通过 plugin 命令安装的插件。每一个 plugin 命令在开始的时候通过加入runtimepath，告诉 vundle 去激活脚本，注释或者移除这行就会废除插件

    Each `Plugin` command takes a URI pointing to the script. No comments should follow on the same line as the command. Example:
    每个 plugin 命令会使用URI去标中脚本。没有注释会跟在在同一行作为命令
    Plugin 'git_URI'

    The `Plugin` command can optionally take a second argument after the URI. It has to be a dictionary, separated from the URI by a comma. Each key-value pair in the dictionary is a configuration option.
    plugin 命令可以选择性的，在URI后面加入第二个参数，第二个参数需要是一个字典，并且通过逗号与第一个参数隔开。每个字典中的键值对就是一个配置选项

    The following per-script configuration options are available.
    以下的每个脚本配置选项都是可用的

        -- The 'rtp’ option:
        Specifies a directory inside the repository (relative path from the root of the repository) where the vim plugin resides. It determines the path that will be added to the |runtimepath|.
        具体说明vim插件属于repo中的路径或者目录（repo根节点的相对路径）。其决定了加入 runtimepath 中的路径
        For example:
        Plugin 'git_URI', {'rtp': 'some/subdir/'}
        This can be used with git repositories that put the vim plugin inside a subdirectory.
        这个被用于vim插件放在了repo的子目录中

        －－ The 'name’ option:
        The name of the directory that will hold the local clone of the configured script.
        目录的名字将会持有配置的脚本的本地克隆
        For example:
        Plugin 'git_URI', {'name': 'newPluginName'}
        This can be used to prevent name collisions between plugins that Vundle would otherwise try to clone into the same directory. It also provides an additional level of customisation.
        这个可以被用于防止插件之间的命名冲突，否则 vundle 会将插件放入同一个目录。同时，这也提供了额外层面的定制功能

        －－The 'pinned’ option:
        A flag that, when set to a value of 1, tells Vundle not to perform any git operations on the plugin, while still adding the existing plugin under the `bundles` directories to the |runtimepath|.
        一个标记，当值为1的，将已经存在于bundles目录下的插件路径放入runtimepath的时候，vundle 不会在插件上面执行任何的git操作，
        For example:
        Plugin 'mylocalplugin', {'pinned': 1}
        This allows the users to include, with Vundle, plugins tracked with version control systems other than git, but the user is responsible for cloning and keeping up to date. It also allows the users to stay in the current version of a plugin that might have previously been updated by Vundle.
        这个允许用户通过除了git之外的其他版本控制系统去跟踪插件，但是用户需要对克隆和保持最新负责。它也允许用户保持在一个插件的某个版本，该插件有可能之前被vundle更新过。

        Please note that the URI will be treated the same as for any other plugins, so only the last part of it will be added to the |runtimepath|. The user is advised to use this flag only with single word URIs to avoid confusion.
        请注意，URI会被其他的插件同样的使用，所以只有最后一个使用它的插件会被加入runtimepath。所以建议用户在只有唯一的URI的时候使用这个标记，以免冲突。

    - SUPPORTED URIS
    `Vundle` integrates very well with both GitHub and vim-scripts.org (http://vim-scripts.org/vim/scripts.html) allowing short URIs. It also allows the use of any URI `git` recognizes. In all of the following cases (except local) the 'https' protocol is used, see Vundle's options to override this.

    More information on `git`'s protocols can be found at: http://git-scm.com/book/ch4-1.html

        －－ GitHub
        GitHub is used when a user/repo is passed to `Plugin`.
        Plugin 'VundleVim/Vundle.vim' => https://github.com/VundleVim/Vundle.vim

        －－ Vim Scripts
        Any single word without a slash '/' is assumed to be from Vim Scripts.
        Plugin 'ctrlp.vim' => https://github.com/vim-scripts/ctrlp.vim

        －－ Other Git URIs
        No modification is performed on valid URIs that point outside the above URLs.
        Plugin 'git://git.wincent.com/command-t.git'

        －－ Local Plugins
        The git protocol supports local installation using the 'file://' protocol. This is handy when developing plugins locally. Follow the protocol with an absolute path to the script directory.
        Plugin 'file:///path/from/root/to/plugin'

    - INSTALLING PLUGINS
    :PluginInstall
    Will install all plugins configured in your `.vimrc`. Newly installed plugins will be automatically enabled. Some plugins may require extra steps such as compilation or external programs, refer to their documentation.

    PluginInstall allows installation of plugins by name:
    :PluginInstall unite.vim
    Installs and activates unite.vim.

    PluginInstall also allows installation of several plugins separated by space.
    :PluginInstall tpope/vim-surround tpope/vim-fugitive
    Installs both tpope/vim-surround and tpope/vim-fugitive from GitHub.

    You can use Tab to auto-complete known script names.
    Note that the installation just described isn't permanent. To finish, you must put `Plugin 'unite.vim'` at the appropriate place in your `.vimrc` to tell Vundle to load the plugin at startup.

    After installing plugins press 'l' (lowercase 'L') to see the log of commands if any errors occurred.

    - UPDATING PLUGINS
        :PluginInstall!   " NOTE: bang(!)
    or
        :PluginUpdate

    Installs or updates the configured plugins. Press 'u' after updates complete to see the change log of all updated bundles. Press 'l' (lowercase 'L') to see the log of commands if any errors occurred.
    To update specific plugins, write their names separated by space:
        :PluginInstall! vim-surround vim-fugitive
    or
        :PluginUpdate vim-surround vim-fugitive

    - SEARCHING PLUGINS
    :PluginSearch
    Search requires that `curl` be available on the system. The command searches Vim Scripts (http://vim-scripts.org/vim/scripts.html) for matching plugins. Results display in a new split window. For example:
    PluginSearch foo
    displays:
        "Search results for: foo
        Plugin 'MarkdownFootnotes'
        Plugin 'VimFootnotes'
        Plugin 'foo.vim'

    Alternatively, you can refresh the script list before searching by adding a bang to the command.
        :PluginSearch! foo

    If the command is run without argument:
        :PluginSearch!
    it will display all known plugins in the new split.

    - LISTING BUNDLES
    :PluginList
    Displays a list of installed bundles.

    - CLEANING UP
    :PluginClean
    Requests confirmation for the removal of all plugins no longered configured in your `.vimrc` but present in your bundle installation directory (default: `.vim/bundle/`).

    :PluginClean!
    Automatically confirm removal of unused bundles.

4. INTERACTIVE MODE ~
    Vundle provides a simple interactive mode to help you explore new plugins easily.  Interactive mode is available after any command that lists `Plugins` such as PluginSearch, PluginList or Plugins. For instance:
    :PluginSearch! unite

    Searches for plugins matching 'unite' and yields a split window with:
        "Keymap: i - Install bundle; c - Cleanup; s - Search; R - Reload list
        "Search results for: unite
        Plugin 'unite-scriptenames'
        Plugin 'unite.vim'
        Plugin 'unite-yarm'
        Plugin 'unite-gem'
        Plugin 'unite-locate'
        Plugin 'unite-font'
        Plugin 'unite-colorscheme'

    To install a bundle, move your cursor to the Plugin of interest and then select a command. To install 'unite.vim' put your cursor on the line and then push `i`. For a more complete list see |vundle-keymappings|. After unite.vim is installed the `:Unite file` command should be available.
    Note: Interactive installation doesn't update your `.vimrc`.

5. KEY MAPPINGS ~
    KEY | DESCRIPTION
    ----|-------------------------- >
     i  |  run :PluginInstall with name taken from line cursor is positioned on
     I  |  same as i, but runs :PluginInstall! to update bundle
     D  |  delete selected bundle (be careful not to remove local modifications)
     c  |  run :PluginClean
     s  |  run :PluginSearch
     R  |  fetch fresh script list from server

6. OPTIONS ~
    let g:vundle_default_git_proto = 'git'
    This option makes Vundle use `git` instead of `https` when building
    absolute URIs. For example:
    Plugin 'sjl/gundo.vim' -> git@github.com:sjl/gundo.git

7. VUNDLE INTERFACE CHANGE ~
                        *vundle-interface-change* *:Bundle* *:BundleInstall!*
                *:BundleUpdate* *:BundleSearch* *:BundleList* *:BundleClean!*
                            *:VundleInstall!* *:VundleUpdate* *:VundleSearch*
                                                *:VundleList* *:VundleClean!*

  In order to bring in new changes, Vundle is adopting a new interface. Going forward we will support primarily the Plugin namespace, additionally for convenience we will also alias some commands to the Vundle namespace. The following table summarizes the interface changes.
      Deprecated Names  | New Names
      -----------------------------
      Bundle            | Plugin
      BundleInstall(!)  | PluginInstall(!), VundleInstall(!)
      BundleUpdate      | PluginUpdate, VundleUpdate
      BundleSearch(!)   | PluginSearch(!), VundleSearch(!)
      BundleClean       | PluginClean(!), VundleClean(!)
      BundleList        | PluginList

  Note: The Bundle commands will be deprecated. You may continue using them, but they may not get all future updates. For instance, we have enabled comments on Plugin lines but not Bundle, since it requires a change in command declaration.
" vim: set expandtab sts=2 ts=2 sw=2 tw=78 ft=help norl:
