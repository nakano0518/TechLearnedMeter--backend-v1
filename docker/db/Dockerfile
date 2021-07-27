FROM postgres:13.3
# デフォルトでサーバーロケールがen_US.utf8
# ja_JP.utf8が選択肢として存在しないので下記で追加
RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8
# LANG環境変数にja_JP.utf8をセット
ENV LANG ja_JP.utf8
