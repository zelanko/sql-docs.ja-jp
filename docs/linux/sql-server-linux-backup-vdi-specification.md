---
title: SQL Server on Linux の VDI バックアップ仕様 |Microsoft Docs
description: SQL Server バックアップの仮想デバイス インターフェイスの仕様。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 0250ba2b-8cdd-450e-9109-bf74f70e1247
ms.openlocfilehash: b3917f086361128ee0c3e0a73f44f2c7cc4049b6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713469"
---
# <a name="sql-server-on-linux-vdi-client-sdk-specification"></a>SQL Server Linux VDI クライアント SDK の仕様

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、SQL Server on Linux の仮想デバイス インターフェイス (VDI) クライアント SDK によって提供されるインターフェイスについて説明します。 独立系ソフトウェア ベンダー (Isv) は、自社製品に SQL Server を統合するのに、仮想バックアップ デバイス アプリケーション プログラミング インターフェイス (API) を使用することができます。 一般に、Linux 上の VDI と同様に動作 Windows での VDI で、次の変更。

- Windows 共有メモリでは、POSIX 共有メモリになります。
- Windows のセマフォは、POSIX セマフォになります。
- HRESULT と DWORD などの Windows は、対応する整数値に変更されます。
- COM インターフェイスが削除され、C++ クラスのペアに置き換えられます。
- Linux 上の SQL Server が名前付きインスタンスをサポートしていないインスタンス名への参照が削除されたためです。 
- 共有ライブラリは/opt/mssql/lib/libsqlvdi.so にインストールされている libsqlvdi.so で実装します。

このドキュメントは、補遺**vbackup.chm** Windows VDI の仕様の詳細を含むです。 ダウンロード、 [Windows VDI 仕様](https://www.microsoft.com/download/details.aspx?id=17282)します。

サンプルの VDI バックアップ ソリューションを確認することも、 [SQL Server のサンプル GitHub リポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sqlvdi-linux)します。

## <a name="user-permissions-setup"></a>ユーザーのアクセス許可の設定

Linux では、POSIX プリミティブは、それらとその既定のグループを作成するユーザーによって所有されます。 SQL Server によって作成されたオブジェクトでは、これらが既定で所有する mssql ユーザーと mssql グループ。 SQL サーバーと VDI クライアント間で共有できるように、次の 2 つのメソッドの 1 つを推奨します。

1. VDI クライアントを mssql ユーザーとして実行します。
   
   Mssql ユーザーに切り替えるには、次のコマンドを実行します。
   
   ```bash
   sudo su mssql
   ```

2. Vdiuser のグループ、および mssql グループに vdiuser を mssql ユーザーを追加します。
   
   次のコマンドを実行します。

   ```bash
   sudo useradd vdiuser
   sudo usermod -a -G mssql vdiuser
   sudo usermod -a -G vdiuser mssql
   ```

   SQL Server および vdiuser の新しいグループを選択するサーバーを再起動します。

## <a name="client-functions"></a>クライアントの機能

この章には、各クライアントの機能の説明が含まれています。 説明には、次の情報が含まれます。

- 関数の目的
- 関数の構文
- パラメーター リスト
- 戻り値
- コメント

## <a name="clientvirtualdevicesetcreate"></a>ClientVirtualDeviceSet::Create

**目的**この関数は、仮想デバイスのセットを作成します。

**構文**
   ```
   int ClientVirtualDeviceSet::Create (
   char *   name,       // name for the set
   VDConfig   * cfg     // configuration for the set
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| | **name** | これは、仮想デバイスのセットを識別します。 CreateFileMapping() で使用される名前の規則に従う必要があります。 円記号を除く任意の文字 (\)使用可能性があります。 これは、文字の文字列です。 文字列とユーザーの製品や会社名とデータベース名を付けることをお勧めします。 |
| |**cfg** | これは、仮想デバイスのセットを構成します。 詳細については、このドキュメントの後半の「構成」を参照してください。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** | 関数が正常に実行されました。 |
| |**VD_E_NOTSUPPORTED** |構成内のフィールドの 1 つ以上が無効か、それ以外の場合にサポートされていません。 |
| |**VD_E_PROTOCOL** | 仮想デバイス セットが既に存在します。

**「解説」** の作成の方法はバックアップまたは復元操作あたり 1 回だけ呼び出す必要があります。 Close メソッドを呼び出した後、クライアントは、別の仮想デバイスのセットを作成するには、インターフェイスを再利用できます。

## <a name="clientvirtualdevicesetgetconfiguration"></a>ClientVirtualDeviceSet::GetConfiguration

**目的**この関数を使用して、サーバーが仮想デバイスの設定を構成するまで待機します。
**構文**
   ```
   int ClientVirtualDeviceSet::GetConfiguration (
   time_t       timeout,    // in milliseconds
   VDConfig *       cfg // selected configuration
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| | **timeout** | これは、ミリ秒単位のタイムアウトです。 タイムアウトを防ぐために無限または任意の負の整数を使用します。
| | **cfg** | 正常に実行すると、サーバーによって選択された構成が含まれます。 詳細については、このドキュメントの後半の「構成」を参照してください。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** | 構成が返されました。
| |**VD_E_ABORT** |SignalAbort が呼び出されました。
| |**VD_E_TIMEOUT** |関数がタイムアウトしました。

**「解説」** アラートの状態でこの関数をブロックします。 成功の呼び出しの後に仮想デバイスのセット内のデバイスを開くことができます。


## <a name="clientvirtualdevicesetopendevice"></a>ClientVirtualDeviceSet::OpenDevice
**目的**この関数は、デバイスのいずれかで仮想デバイスのセットが表示されます。
**構文**
   ```
   int ClientVirtualDeviceSet::OpenDevice (
   char *           name,       // name for the set
   ClientVirtualDevice **       ppVirtualDevice // returns interface to device
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| | **name** |これは、仮想デバイスのセットを識別します。
| | **ppVirtualDevice** |関数が成功すると、仮想デバイスへのポインターが返されます。 このデバイスは、get コマンドと CompleteCommand に使用されます。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_ABORT** | Abort が要求されました。
| |**VD_E_OPEN** |  すべてのデバイスは、開いています。
| |**VD_E_PROTOCOL** |  セットが初期化状態がないか、この特定のデバイスが既に開いています。
| |**VD_E_INVALID** |デバイス名が無効です。 ないのセットを構成する既知の名前。

**「解説」** VD_E_OPEN を問題なく返される可能性があります。 クライアントは、このコードが返されるまでループを使用して OpenDevice を呼び出すことができます。
かどうか 1 つ以上のデバイスの構成が、たとえば*n*デバイス、仮想デバイスのセットを返します*n*一意のデバイスのインターフェイス。

`GetConfiguration`デバイスを開くことができるまで待機する関数を使用できます。
この関数が成功しなかった場合、null 値が、ppVirtualDevice を介して返されます。
 
## <a name="clientvirtualdevicegetcommand"></a>ClientVirtualDevice::GetCommand

**目的**この関数を使用して、[次へ] を取得するコマンドをデバイスにキューに登録します。 要求されると、この関数は、次のコマンドを待機します。

**構文**
   ```
   int ClientVirtualDevice::GetCommand (
   time_t       timeout,    // time-out in milliseconds
   VDC_Command**    ppCmd   // returns the next command
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**timeout** |これは、ミリ秒単位の待機時間です。 無限を使用して、無期限に待機します。 コマンドをポーリングするには、0 を使用します。 コマンドが現在使用できない場合は、VD_E_TIMEOUT が返されます。 タイムアウトが発生した場合、クライアントは、次のアクションを決定します。
| |**Timeout** |これは、ミリ秒単位の待機時間です。 無制限に待機するには、無限または負の値を使用します。 コマンドをポーリングするには、0 を使用します。 コマンドが使用できない場合、タイムアウトの有効期限が切れる前に、VD_E_TIMEOUT が返されます。 タイムアウトが発生した場合、クライアントは、次のアクションを決定します。
| |**ppCmd** |コマンドが正常に返されると、パラメーターは、実行するコマンドのアドレスを返します。 返されるメモリは読み取り専用です。 コマンドが完了したら、このポインターは CompleteCommand ルーチンに渡されます。 詳細については、各コマンドは、このドキュメントの後半の「コマンド」を参照してください。
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |コマンドがフェッチされました。
| |**VD_E_CLOSE** |デバイスがサーバーによって閉じられました。
| |**VD_E_TIMEOUT** |コマンドがなかった、タイムアウトになりました。
| |**VD_E_ABORT** |クライアントまたはサーバーに、シャット ダウンを強制するのに、SignalAbort が使用します。

**「解説」** ときれましたが返され、SQL Server には、デバイスが閉じられています。 これは、通常のシャット ダウンの一部です。 すべてのデバイスが閉じられると、クライアントは、仮想デバイスのセットを閉じる ClientVirtualDeviceSet::Close を呼び出します。
このルーチンは、コマンドの待機をブロックする必要があります、スレッドが Alertable 状態のままです。

## <a name="clientvirtualdevicecompletecommand"></a>ClientVirtualDevice::CompleteCommand

**目的**コマンドが完了した SQL サーバーに通知するこの関数を使用します。 コマンドの適切な完了の情報が返されます。 詳細については、このドキュメントで後述する「コマンド」を参照してください。

**構文** 

   ```
   int ClientVirtualDevice::CompleteCommand (
   VDC_Command pCmd,        // the command
   int  completionCode,     // completion code
   unsigned long    bytesTransferred,   // bytes transferred
   int64_t  position        // current position
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**pCmd** |これは以前 ClientVirtualDevice::GetCommand から返されたコマンドのアドレスです。
| |**completionCode** |これは、完了ステータスを示すステータス コードです。 すべてのコマンドは、このパラメーターを返す必要があります。 返されたコードを実行中のコマンドを適切なことがあります。 ERROR_SUCCESS は、すべてのケースでを正常に実行されたコマンドを示すために使用されます。 可能なコードの完全な一覧で、ファイルを参照してください。 vdierror.h します。 このドキュメントの後半で、「コマンド」の各コマンドの一般的なステータス コード一覧が表示されます。
| |**bytesTransferred** |これは、正常に転送されたバイト数です。 これは、データ転送のコマンドは、読み取りし、書き込みに対してのみ返されます。
| |**position** |これは、応答の GetPosition コマンドのみを示します。
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |完了が正しく記述されています。
| |**VD_E_INVALID** |pCmd がアクティブなコマンドです。
| |**VD_E_ABORT** |シグナル状態になった中止します。
| |**VD_E_PROTOCOL** |デバイスは開いていません。

**「解説」** なし

## <a name="clientvirtualdevicesetsignalabort"></a>ClientVirtualDeviceSet::SignalAbort

**目的**異常終了を実行することを通知するこの関数を使用します。

**構文** 

   ```
   int ClientVirtualDeviceSet::SignalAbort ();
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |なし | 適用なし
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR**|中止の通知が正常に通知しました。

**「解説」** 、いつでもクライアントのバックアップまたは復元操作を中止する選択可能性があります。 このルーチンは、すべての操作を停止することを通知します。 全体的な仮想デバイスのセットの状態が異常終了した状態になります。 任意のデバイスでのコマンドは返されません。 未完了のすべてのコマンドが自動的に完了、終了コードとして ERROR_OPERATION_ABORTED を返します。 クライアントは、未処理のクライアントに提供されるバッファーの使用が終了しても問題ありません後 ClientVirtualDeviceSet::Close を呼び出す必要があります。 詳細については、このドキュメントで既に「異常終了」を参照してください。

## <a name="clientvirtualdevicesetclose"></a>ClientVirtualDeviceSet::Close

**目的**ClientVirtualDeviceSet::Create によって作成された仮想デバイスのセットを閉じます。 仮想デバイス セットに関連付けられたすべてのリソースのリリースが発生します。

**構文** 

   ```
   int ClientVirtualDeviceSet::Close ();
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |なし |適用なし
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |仮想デバイスのセットが正常に閉じられたときに返されます。
| |**VD_E_PROTOCOL** |仮想デバイスのセットが開かれていませんでしたので、処理は行われません。
| |**VD_E_OPEN** |デバイスがまだ開いていました。

**「解説」** Close 呼び出しは、仮想デバイスのセットによって使用されるすべてリソースを解放する必要があるクライアントの宣言。 クライアントは、Close を呼び出す前にデータ バッファーおよび仮想デバイスに関連するすべてのアクティビティが終了することを確認する必要があります。 閉じる OpenDevice によって返されるすべての仮想デバイス インターフェイスは無効にします。
Close の呼び出しが返された後、仮想デバイスのセットのインターフェイスの作成の呼び出しを発行するクライアントが許可されます。 このような呼び出しでは、後続のバックアップまたは復元操作用に設定し、新しい仮想デバイスを作成します。
1 つまたは複数の仮想デバイスをまだ開いているときに Close が呼び出される場合は、VD_E_OPEN が返されます。 この場合、SignalAbort が、適切なシャット ダウン可能であれば、内部的にトリガーされます。 VDI のリソースが解放されます。 ClientVirtualDeviceSet::Close を呼び出す前に各デバイスでれましたは、クライアントが待機する必要があります。 クライアントいることを認識仮想デバイスのセットが既に異常終了した状態にし、共有バッファーでアクティビティを終了するとすぐ、ClientVirtualDeviceSet::Close を呼び出すことができ、get コマンドかられました indication は期待できません。
詳細については、このドキュメントで既に「異常終了」を参照してください。

## <a name="clientvirtualdevicesetopeninsecondary"></a>ClientVirtualDeviceSet::OpenInSecondary

**目的**この機能は、仮想デバイスでは、セカンダリのクライアント設定を開きます。 プライマリ クライアント既に使用していなければなりません GetConfiguration の作成と仮想デバイスのセットを設定します。

**構文** 
   
   ```
   int ClientVirtualDeviceSet::OpenInSecondary (
   char *   setName         // name of the set
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**setName** |これは、セットを識別します。 この名前は小文字は区別され、ClientVirtualDeviceSet::Create が呼び出されたときに、プライマリ クライアントによって使用される名前に一致する必要があります。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_PROTOCOL** |仮想デバイスのセットが作成されていない、このクライアントでは、または仮想デバイスで既に開かれているセットがセカンダリのクライアントからのオープン要求を受け入れる準備ができていません。
| |**VD_E_ABORT** |操作を中止しています。

**「解説」** セカンダリ クライアントの通常および異常な終了を検出するため、プライマリ クライアント複数のプロセス モデルを使用する場合。

## <a name="clientvirtualdevicesetgetbufferhandle"></a>ClientVirtualDeviceSet::GetBufferHandle

**目的**いくつかのアプリケーションには、ClientVirtualDevice::GetCommand によって返されたバッファーで動作する 1 つ以上のプロセスが必要です。 このような場合は、コマンドを受信するプロセスは、バッファーを識別するプロセスの独立したハンドルを取得する GetBufferHandle を使用できます。 このハンドルを持つ、同じ仮想デバイスのセットを開いてその他のプロセスに伝達できます。 そのプロセスには、バッファーのアドレスを取得するのに ClientVirtualDeviceSet::MapBufferHandle し使用します。 各プロセスが別のアドレスにバッファーをマッピングするためアドレスはそのパートナーのさまざまなアドレスとする可能性があります。

**構文** 

   ```
   int ClientVirtualDeviceSet::GetBufferHandle (
   uint8_t*     pBuffer,        // in: buffer address
   unsigned int*        pBufferHandle   // out: buffer handle
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**pBuffer** |これは、読み取りまたは書き込みコマンドから取得したバッファーのアドレスです。
| |**BufferHandle** |バッファーの一意の識別子が返されます。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_PROTOCOL** |仮想デバイスのセットが現在開いていません。
| |**VD_E_INVALID** |PBuffer が有効なアドレスではありません。

GetBufferHandle 関数を呼び出すプロセスは、データ転送が完了すると、ClientVirtualDevice::CompleteCommand を呼び出すことを解説します。

## <a name="clientvirtualdevicesetmapbufferhandle"></a>ClientVirtualDeviceSet::MapBufferHandle

**目的**他のプロセスから取得したバッファー ハンドルの有効なバッファーのアドレスを取得するこの関数を使用します。 

**構文** 

   ```
   int ClientVirtualDeviceSet::MapBufferHandle (
   i        nt  dwBuffer,   // in: buffer handle
   uint8_t**    ppBuffer        // out: buffer address
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**dwBuffer** |これは、ClientVirtualDeviceSet::GetBufferHandle によって返されたハンドルです。
| |**ppBuffer** |これは、現在のプロセスでは有効であるバッファーのアドレスです。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_PROTOCOL** |仮想デバイスのセットが現在開いていません。
| |**VD_E_INVALID** |PpBuffer は、無効なハンドルです。

**「解説」** ハンドル正常に通信注意おく必要があります。 ハンドルは、1 つの仮想デバイスのセットに対してローカルです。 ハンドルを共有するパートナーのプロセスには、そのバッファー ハンドルは、仮想デバイスから、バッファーが最初に取得されたセットのスコープ内でのみ使用する必要がありますを確認します。


