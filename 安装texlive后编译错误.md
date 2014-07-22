安装texlive 2014后编译中文出现一下错误

    !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
    !
    ! 
    ! The font "[SIMKAI.TTF]" cannot be found.
    ! 
    ! See the fontspec documentation for further information.
    ! 
    ! For immediate help type H <return>.
    !............................................... 

只需要修改如下文件`/usr/local/texlive/2014/texmf-dist/tex/latex/ctex/fontset/ctex-xecjk-winfonts.def`
将`[SimKai.TTF]`替换为`KaiTi`，注意中括号要去掉

