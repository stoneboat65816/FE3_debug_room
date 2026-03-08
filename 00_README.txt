==============Mục lục/目次/TABLE OF CONTENTS============

A. Tiếng Việt
	I. Khái quát
	II. Cấu trúc
	III. Cách compile
	
B. 日本語
	I. 概要
	II. 本フォルダーの構造成分
	III. 実行方法
	
C. English
	I. Overview
	II. Structure
	III. How to Compile

########################   A. Tiếng Việt   ###################################
I. Khái quát
Đây là mã nguồn mở khóa Debug-room trong trò chơi điện tử "Fire Emblem Monshō no Nazo" （ファイアーエムブレム紋章の謎/Mộc đế Chiến kỷ 3）được phát hành cho máy chơi game Nintendō Super Famicom vào năm 1994.
Trong giai đoạn phát triển, nhà sản xuất đã tạo ra một Debug-room để kiểm tra chức năng của các trận đấu, nhưng nó đã bị khóa lại trong bản thương mại.
Với mã nguồn này, bạn có thể tự compile Rom gốc (tiếng Nhật) để mở khóa chức năng này chỉ với một cú click chuột.
Mã nguồn này được thiết kế để chạy trên Windows. Nếu muốn chạy trên Mac thì bạn cần phải chạy thông qua WINE hoặc máy ảo.

II. Cấu trúc
Folder mã nguồn này gồm những thành phần như bên dưới, không tính file Readme này.
◆01_enable_debug_room.txt: file chứa code để mở khóa chức năng Debug-room. Mở/chỉnh sửa nó bằng bất kỳ phần mềm text-editor nào, chẳng hạn như Notepad có sẵn trên Windows.
◆01_xkas.exe (tác giả: Byuu): phần mềm biến mã assembly trong file "01_enable_debug_room.txt" thành mã máy rồi chèn chúng vào Rom. 
◆01_run.bat: file batch của Windows, dùng để gọi xkas. Double click file này để chạy.

Trong folder này không bao gồm Rom. 
Nếu bạn sở hữu băng game một cách hợp pháp thì có thể trích xuất Rom từ băng qua các thiết bị như Super UFO PRO 8.

III. Cách compile

1. Mở file "01_run.bat" bằng phần mềm Notepad hoặc bất kỳ text-editor nào.
Trong này bạn sẽ thấy những dòng lệnh như bên dưới.

=============Code===============
copy 01_FE3.sfc 01_FE3_debug.sfc
01_xkas.exe -o 01_FE3_debug.sfc 01_enable_debug_room.txt
pause
================================

Trong đó "01_FE3.sfc" là tên Rom gốc chưa chỉnh sửa, còn "01_FE3_debug.sfc" là tên bản sao của Rom gốc.
Bạn có thể đổi tên Rom thành bất cứ tên gì cũng được, miễn là nó khớp với phần khai báo trong file .bat này.
Chúng ta làm việc trên bản sao của Rom để tránh gây ảnh hưởng lên Rom gốc.

2. Đặt Rom gốc (tiếng Nhật) của trò "Fire Emblem Monshō no Nazo" vào folder này.

3. Double-click vào file "01_run.bat". Lúc này xkas sẽ tạo ta file "01_FE3_debug.sfc" (hoặc bất kỳ tên gì, ứng với tên được khai báo ở bước 1).

4. Chạy file "01_FE3_debug.sfc" vừa được tạo ra bằng các phần mềm giả lập Super Famicom như BSNES, MESEN, SNES9X,...
Bạn cũng có thể chạy file này trên phần cứng Super Famicom thật hoặc những phần cứng clone khác như SupaBoy, Retron,...

5. Trong game, sau khi di chuyển nhân vật, hãy nhấn giữ nút Select rồi chọn một trong các command bất kỳ như "tấn công", "đợi"... để kích hoạt Debug-room.
Bạn có thể chỉnh sửa mã nguồn để thay đổi nút bấm kích hoạt Debug-room.

Lưu ý: Rom gốc của bạn không được chứa 0x0200 byte header.
Dùng bất cứ Hex-editor nào để kiểm tra. Nếu thấy phần header thì xóa nó đi.

Mã nguồn được chia sẻ miễn phí tại:
https://github.com/stoneboat65816/

########################   B. 日本語   ###################################
I. 概要
これは、1994年に任天堂の家庭用ゲーム機スーパーファミコン向けに発売された『ファイアーエムブレム 紋章の謎』の（デバッグルーム）を有効化するためのソースコードです。
開発段階では、戦闘シーンの動作を確認するためにこのデバッグルームが作成されたが、製品版ではこの機能は無効化されました。
本ソースコードを使用することで、無改造ROM（日本語版）を対象としてワンクリックで当該機能を解放することができます。
このソースコードおよび関連ソフトはWindows上で動作させるよう設計されています。MacOSで実行する場合は、WINEまたは仮想マシンを使用してください。

II. 本フォルダーの構造成分
本ソースコードフォルダーには、本Readmeファイルを除き、以下の内容が含まれています。
■01_enable_debug_room.txt：デバッグルーム機能を解放するためのコードを収録したファイルです。Windowsに搭載されているNotepadなど、任意のテキストエディタで開いたり編集したりできます。
■01_xkas.exe（作者：Byuu氏）：「01_enable_debug_room.txt」内のアセンブリコードを機械語へ変換し、ROMへ挿入するソフトウェアです。
■01_run.bat：Windows用のバッチファイルで、xkasを呼び出すために使用します。本ファイルをダブルクリックすることで実行できます。

本フォルダーにはROMファイルは含まれていません。
ゲームカセットを所有している場合、Super UFO PRO 8などの吸出し器を使用することでカセットからROMを抽出することが可能です。

III. 実行方法
1. 「01_run.bat」ファイルを、Notepadまたは任意のテキストエディタで開いてください。
ファイル内には、以下のようなコマンド行が記載されています。
=============Code===============
copy 01_FE3.sfc 01_FE3_debug.sfc
01_xkas.exe -o 01_FE3_debug.sfc 01_enable_debug_room.txt
pause
================================
ここで、「01_FE3.sfc」は無改造ROMのファイル名で、「01_FE3_debug.sfc」はそのコピーのファイル名です。
ROMのファイル名は任意の名称に変更可能ですが、その場合は本.batファイル内で指定されている名称と一致させる必要があります。
無改造ROMに影響を与えないよう、本作業は必ずそのコピーを対象にして行ってください。

2 .無改造ROMの日本語版『ファイアーエムブレム 紋章の謎』を本フォルダー内に置いてください。

3. 「01_run.bat」をダブルクリックします。
すると、xkasにより「01_FE3_debug.sfc」（または1.で指定した任意のファイル名）が生成されます。

4. 生成された「01_FE3_debug.sfc」を、bsnes、Mesen、Snes9x などのスーパーファミコン用エミュレータでプレイしてください。
また、スーパーファミコン実機や、SupaBoy、Retron などの互換機で動作させることも可能です。

5. ゲーム内でユニットを移動させた後、Selectボタンを押し続けながら、「攻撃」「待機」など任意のコマンドを選択すると、Debug-roomが起動します。
なお、ソースコードを編集することで、Debug-roomを起動するボタンの割り当てを変更することも可能です。

※無改造ROMは、ヘッダー（0x200バイト）のないものでないといけません。スターリング等バイナリエディタでROMを開いてヘッダーの有無を確認できます。ヘッダーが確認された場合、バイナリエディタで削除してください。

このソースコードは下記URLにて無料で提供しております。
https://github.com/stoneboat65816/


########################   C. English   ###################################
I. Overview
This is the source code for unlocking the hidden Debug Room in the video game Fire Emblem: Monshō no Nazo (ファイアーエムブレム紋章の謎/Mystery of the Emblem), released for the Super Famicom back in 1994.
During development, the creators included a Debug Room to test battle mechanics and various game functions, but it was locked in the final retail version.
With this source code, you can compile the original Japanese ROM yourself and unlock this feature with just a single click.
This source code is designed to run on Windows. If you’re on a Mac, you’ll need to run it through WINE or a virtual machine.

II. Structure
This source folder includes the following files (not counting this Readme):
■01_enable_debug_room.txt – This file contains the code used to unlock the Debug Room. You can open and edit it with any text editor, like the built-in Notepad on Windows.
■01_xkas.exe (author: Byuu) – This tool assembles the assembly code from 01_enable_debug_room.txt into machine code and inserts it into the ROM.
■01_run.bat – A Windows batch file used to run xkas. Just double-click this file to execute it.

The ROM file itself is not included in this folder.
If you legally own the original game cartridge, you can dump the ROM using devices such as the Super UFO PRO 8.

III. How to Compile

1. Open the file “01_run.bat” using Notepad or any text editor.
Inside, you’ll see lines of code like the ones below.

=============Code===============
copy 01_FE3.sfc 01_FE3_debug.sfc
01_xkas.exe -o 01_FE3_debug.sfc 01_enable_debug_room.txt
pause
================================
In that file, "01_FE3.sfc" is the name of the original, unmodified ROM, and "01_FE3_debug.sfc" is the name of the duplicated ROM that will be patched.
You can rename the ROM to anything you like, as long as it matches what’s written in the .bat file.
We’re working on a copy of the ROM to make sure the original file stays untouched.

2. Place the original Japanese ROM of Fire Emblem: Monshō no Nazo into this folder.

3. Double-click “01_run.bat.”
xkas will then generate a new file called “01_FE3_debug.sfc” (or whatever name you specified in step 1).

4. Run the newly created ROM file using a Super Famicom emulator such as bsnes, Mesen, or SNES9x.
You can also run it on real Super Famicom hardware or compatible clone systems like SupaBoy or RetroN.

5. In-game, after moving a character, hold the Select button and then choose any command like "Attack" or "Wait" to activate the Debug Room.
You can modify the source code to change the button used to activate the Debug Room.

Note: the untouched ROM must be a headerless one. You can open the ROM using any Hex-editor to comfirm whether it has 0x200 bytes header or not.
If it does, you must delete this header using the Hex-editor.

The source code is available for free at:
https://github.com/stoneboat65816/