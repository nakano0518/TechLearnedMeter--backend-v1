FROM postgres:13.3
# デフォルトでサーバーロケールがen_US.utf8なので変更
RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8
# LANG環境変数にもja_JP.utf8を入れておく
ENV LANG ja_JP.utf8
