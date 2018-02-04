---
title: "VDI のバックアップ Specification - SQL Server on Linux |Microsoft ドキュメント"
description: "SQL Server のバックアップの仮想デバイス インターフェイス仕様です。"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 0250ba2b-8cdd-450e-9109-bf74f70e1247
ms.workload: Inactive
ms.openlocfilehash: fc2fa01902fee76b85c4b348d701166845a6d95e
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="sql-server-on-linux-vdi-client-sdk-specification"></a>Linux VDI クライアント SDK 仕様 SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Linux 仮想デバイス インターフェイス (VDI) クライアント SDK 上の SQL Server によって提供されるインターフェイスについて説明します。 独立系ソフトウェア ベンダー (Isv) は、仮想バックアップ デバイス アプリケーション プログラミング インターフェイス (API) を使用して、各自の製品に SQL Server を統合します。 一般に、Linux での VDI と同様に動作 VDI Windows 上で、次の変更。

- Windows 共有メモリでは、POSIX 共有メモリになります。
- Windows のセマフォでは、POSIX セマフォになります。
- HRESULT および DWORD のように Windows の種類は、同等の整数に変更されます。
- COM インターフェイスは削除され、C++ クラスのペアに置き換えられます。
- SQL Server on Linux は、名前付きインスタンスにはサポートしないため、インスタンス名への参照が削除されました。 
- 共有ライブラリは/opt/mssql/lib/libsqlvdi.so にインストールされている libsqlvdi.so に実装します。

このドキュメントは、付録**vbackup.chm** Windows VDI 仕様の詳細を含むです。 ダウンロード、 [Windows VDI 仕様](http://www.microsoft.com/download/details.aspx?id=17282)です。

サンプル VDI のバックアップ ソリューションを確認しても、 [SQL Server のサンプルの GitHub リポジトリ](http://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sqlvdi-linux)です。

## <a name="user-permissions-setup"></a>ユーザーのアクセス許可の設定

Linux では、POSIX プリミティブは、その既定のグループを作成するユーザーによって所有されます。 、SQL Server によって作成されたオブジェクトに対してこれらは既定で所有 mssql ユーザーと mssql グループです。 SQL Server と VDI クライアント間で共有できるように、次の 2 つのメソッドのいずれかが推奨されます。

1. Mssql ユーザーとして VDI クライアントを実行します。
   
   Mssql ユーザーに切り替えるには、次のコマンドを実行します。
   
   ```bash
   sudo su mssql
   ```

2. Vdiuser のグループ、および vdiuser mssql グループにするには、mssql ユーザーを追加します。
   
   次のコマンドを実行します。

   ```bash
   sudo useradd vdiuser
   sudo usermod -a -G mssql vdiuser
   sudo usermod -a -G vdiuser mssql
   ```

   SQL Server および vdiuser 用の新しいグループを取得するサーバーを再起動します。

## <a name="client-functions"></a>クライアントの機能

この章には、各クライアントの機能の説明が含まれています。 説明については、次のとおりです。

- 関数の目的
- 関数の構文
- パラメーター リスト
- 戻り値
- 解説

## <a name="clientvirtualdevicesetcreate"></a>ClientVirtualDeviceSet::Create

**目的**この関数は、仮想デバイス セットを作成します。

**構文**
   ```
   int ClientVirtualDeviceSet::Create (
   char *   name,       // name for the set
   VDConfig   * cfg     // configuration for the set
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| | **name** | これは、仮想デバイス セットを識別します。 CreateFileMapping() によって使用される名前の規則に従う必要があります。 バック スラッシュを除く任意の文字 (\)使用可能性があります。 これは、文字の文字列です。 ユーザーの製品または組織の名前とデータベース名を持つ文字列をプレフィックスとして付けることをお勧めします。 |
| |**cfg** | これは、仮想デバイス セットを構成します。 詳細については、このドキュメントで後述の「構成」を参照してください。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** | 関数が正常に実行されました。 |
| |**VD_E_NOTSUPPORTED** |1 つ以上の構成内のフィールドが無効か、サポートされています。 |
| |**VD_E_PROTOCOL** | 仮想デバイス セットが既に存在します。

**「解説」**バックアップまたは復元操作ごとに、作成方法を 1 回だけ呼び出す必要があります。 Close メソッドを呼び出した後、クライアントは、別の仮想デバイス セットを作成するには、インターフェイスを再利用できます。

## <a name="clientvirtualdevicesetgetconfiguration"></a>ClientVirtualDeviceSet::GetConfiguration

**目的**この関数は、仮想デバイス セットを構成するサーバーの待機に使用します。
**構文**
   ```
   int ClientVirtualDeviceSet::GetConfiguration (
   time_t       timeout,    // in milliseconds
   VDConfig *       cfg // selected configuration
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| | **timeout** | これは、ミリ秒単位のタイムアウトです。 タイムアウトを防ぐために無限または負の値の任意の整数を使用します。
| | **cfg** | 正常に実行すると、サーバーが選択した設定が含まれます。 詳細については、このドキュメントで後述の「構成」を参照してください。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** | 構成が返されました。
| |**VD_E_ABORT** |SignalAbort が呼び出されました。
| |**VD_E_TIMEOUT** |関数がタイムアウトしました。

**「解説」**アラート可能な状態でこの関数をブロックします。 成功した呼び出しでは、後に仮想デバイス セット内のデバイスを開くことができます。


## <a name="clientvirtualdevicesetopendevice"></a>ClientVirtualDeviceSet::OpenDevice
**目的**この関数は、デバイスの 1 つの仮想デバイス セットが表示されます。
**構文**
   ```
   int ClientVirtualDeviceSet::OpenDevice (
   char *           name,       // name for the set
   ClientVirtualDevice **       ppVirtualDevice // returns interface to device
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| | **name** |これは、仮想デバイス セットを識別します。
| | **ppVirtualDevice** |関数が成功した場合、仮想デバイスへのポインターが返されます。 このデバイスを使用して、get コマンドと CompleteCommand です。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_ABORT** | Abort が要求されました。
| |**VD_E_OPEN** |  すべてのデバイスは、開いています。
| |**VD_E_PROTOCOL** |  セットが初期化中の状態ではないか、この特定のデバイスが開く既にいます。
| |**VD_E_INVALID** |デバイス名が正しくありません。 できませんのセットを構成する既知の名前。

**「解説」** VD_E_OPEN を問題なく返すことができます。 クライアントは、このコードが返されるまで、ループを使用して OpenDevice を呼び出すことがあります。
かどうか 1 つ以上のデバイスが構成されている、たとえば *n* デバイス、仮想デバイス セットが返されます *n* 一意のデバイスのインターフェイスです。

`GetConfiguration`デバイスを開くことができるまで待機する関数を使用できます。
この関数が成功しなかった場合、null 値が、ppVirtualDevice を介して返されます。
 
## <a name="clientvirtualdevicegetcommand"></a>ClientVirtualDevice::GetCommand

**目的**この関数を使用して、[次へ] を取得するコマンドをデバイスにキューに登録します。 要求された場合、この関数は、次のコマンドを待機します。

**構文**
   ```
   int ClientVirtualDevice::GetCommand (
   time_t       timeout,    // time-out in milliseconds
   VDC_Command**    ppCmd   // returns the next command
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**timeout** |これは、待機する時間 (ミリ秒単位) です。 INFINTE を使用して、無期限に待機します。 コマンドをポーリングするには、0 を使用します。 コマンドが現在使用できない場合は、VD_E_TIMEOUT が返されます。 タイムアウトが発生した場合、クライアントは、次のアクションを決定します。
| |**Timeout** |これは、待機する時間 (ミリ秒単位) です。 無期限に待機する INFINTE または負の値を使用します。 コマンドをポーリングするには、0 を使用します。 コマンドが使用できない場合、タイムアウトの有効期限が切れる前に、VD_E_TIMEOUT が返されます。 タイムアウトが発生した場合、クライアントは、次のアクションを決定します。
| |**ppCmd** |コマンドが正常に返されると、パラメーターは、実行するコマンドのアドレスを返します。 返されるメモリは、読み取り専用です。 コマンドが完了したら、このポインターは CompleteCommand ルーチンに渡されます。 詳細については、各コマンドは、このドキュメントの後半で、「コマンド」を参照してください。
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |コマンドがフェッチされました。
| |**VD_E_CLOSE** |デバイスがサーバーによって閉じられました。
| |**VD_E_TIMEOUT** |コマンドを取得できませんでした、タイムアウトになりました。
| |**VD_E_ABORT** |クライアントまたはサーバーに、シャット ダウンを強制するのに、SignalAbort が使用します。

**「解説」**ときでしたが返され、SQL Server デバイスを閉じました。 これは、通常のシャット ダウンの一部です。 すべてのデバイスが閉じられると、クライアントは、仮想デバイス セットを閉じる ClientVirtualDeviceSet::Close を呼び出します。
このルーチンは、コマンドの待機をブロックする必要があります、ときに、スレッドが、警告状態に残されます。

## <a name="clientvirtualdevicecompletecommand"></a>ClientVirtualDevice::CompleteCommand

**目的**コマンドが完了する SQL Server に通知するこの関数を使用します。 コマンドの適切な完了の情報が返されます。 詳細については、このドキュメントの後半で、「コマンド」を参照してください。

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
| |**completionCode** |これは、完了ステータスを示すステータス コードです。 このパラメーターは、すべてのコマンドを返す必要があります。 返されたコードを実行中のコマンドを適切にする必要があります。 すべてのケースでは、error_success を返しますを使用して正常に実行されたコマンドを表すできます。 コードの完全な一覧をファイルを参照してください。 vdierror.h です。 このドキュメントの後半で、「コマンド」に各コマンドの一般的なステータス コードの一覧が表示されます。
| |**bytesTransferred** |これは、正常に転送されたバイト数です。 これは、コマンドは、読み取りし、書き込みのデータ転送にのみ返されます。
| |**position** |これは、GetPosition コマンドのみへの応答です。
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |完了が正しく記述されています。
| |**VD_E_INVALID** |pCmd はアクティブなコマンドではありませんでした。
| |**VD_E_ABORT** |シグナル状態になった中止します。
| |**VD_E_PROTOCOL** |デバイスは、開かれていません。

**「解説」**なし

## <a name="clientvirtualdevicesetsignalabort"></a>ClientVirtualDeviceSet::SignalAbort

**目的**この関数は、異常終了を実行することを通知に使用します。

**構文** 

   ```
   int ClientVirtualDeviceSet::SignalAbort ();
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |なし | 適用なし
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR**|中止通知が正常に通知しました。

**「解説」** 、いつでもクライアントは、バックアップまたは復元操作を中止できます。 このルーチンは、すべての操作を停止することを通知します。 全体的な仮想デバイス セットの状態が異常終了した状態になります。 任意のデバイスでは、これ以上コマンドは返されません。 すべての未完了のコマンドが自動的に完了すると完了コードとして ERROR_OPERATION_ABORTED を返すことです。 クライアントは、クライアントに提供されるバッファーの未処理を使用するが安全に終了した後、ClientVirtualDeviceSet::Close を呼び出す必要があります。 詳細については、このドキュメントで既に「異常終了」を参照してください。

## <a name="clientvirtualdevicesetclose"></a>ClientVirtualDeviceSet::Close

**目的**ClientVirtualDeviceSet::Create によって作成された仮想デバイスのセットを閉じます。 仮想デバイス セットに関連付けられているすべてのリソースの解放になります。

**構文** 

   ```
   int ClientVirtualDeviceSet::Close ();
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |なし |適用なし
        
| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |仮想デバイス セットが正常に閉じられたときに返されます。
| |**VD_E_PROTOCOL** |仮想デバイス セットが開いていなかったために、処理は行われません。
| |**VD_E_OPEN** |デバイスがまだ開いていました。

**「解説」** Close 呼び出しは、仮想デバイス セットで使用されるすべてのリソースを解放する必要があるクライアント宣言します。 クライアントでは、Close を呼び出す前にデータ バッファーおよび仮想デバイスに関連するすべての活動が終了したことを確認する必要があります。 閉じるでは、OpenDevice によって返されるすべての仮想デバイス インターフェイスが無効になりません。
クライアントは Close の呼び出しが返された後に仮想デバイス セット インターフェイスの作成の呼び出しを発行を許可します。 このような呼び出しでは、新しい仮想デバイスがそれ以降のバックアップまたは復元操作のセットを作成します。
1 つまたは複数の仮想デバイスがまだ開いているときに Close を呼び出すと、VD_E_OPEN が返されます。 この場合、SignalAbort が、適切なシャット ダウン可能であれば、内部的にトリガーされます。 VDI のリソースが解放されます。 クライアントは、ClientVirtualDeviceSet::Close を呼び出す前に各デバイスででした indication の待機する必要があります。 クライアントを把握している場合、仮想デバイス セットが既に、異常終了した状態で、GetCommand からでした示す値を期待できません共有バッファーでアクティビティを終了するとただちに ClientVirtualDeviceSet::Close を呼び出すことがあります。
詳細については、このドキュメントで既に「異常終了」を参照してください。

## <a name="clientvirtualdevicesetopeninsecondary"></a>ClientVirtualDeviceSet::OpenInSecondary

**目的**この関数は、仮想デバイス セカンダリ クライアントのセットを開きます。 主要クライアント必要があります既に使用して作成および GetConfiguration 仮想デバイス セットを設定します。

**構文** 
   
   ```
   int ClientVirtualDeviceSet::OpenInSecondary (
   char *   setName         // name of the set
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**setName** |セットを識別します。 この名前は大文字小文字を区別され、ClientVirtualDeviceSet::Create 呼び出されたときに、プライマリ クライアントで使用する名前に一致する必要があります。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_PROTOCOL** |仮想デバイス セットが作成されていない、このクライアントでは、その仮想デバイスで既に開かれてセットがセカンダリ クライアントからのオープン要求を受け入れる準備ができていません。
| |**VD_E_ABORT** |操作を中止しています。

**「解説」**複数のプロセス モデルを使用する場合、プライマリ クライアントはセカンダリ クライアントの通常および異常終了を検出します。

## <a name="clientvirtualdevicesetgetbufferhandle"></a>ClientVirtualDeviceSet::GetBufferHandle

**目的**一部のアプリケーションが ClientVirtualDevice::GetCommand によって返されたバッファーで動作する 1 つ以上のプロセスを必要があります。 このような場合は、コマンドを受信するプロセスは、バッファーを識別するプロセスの独立したハンドルを取得する GetBufferHandle を使用できます。 このハンドルが、同じ仮想デバイスのセットを開いている他のプロセスに伝えることができます。 そのプロセスが使用して ClientVirtualDeviceSet::MapBufferHandle バッファーのアドレスを取得します。 各プロセスが異なるアドレスでバッファーをマッピングするため、アドレスはそのパートナーの別のアドレスよりもをする可能性があります。

**構文** 

   ```
   int ClientVirtualDeviceSet::GetBufferHandle (
   uint8_t*     pBuffer,        // in: buffer address
   unsigned int*        pBufferHandle   // out: buffer handle
   );
   ```

| パラメーター | 引数 | 説明
| ----- | ----- | ------ |
| |**pBuffer** |これは、読み取りまたは書き込みコマンドを取得するバッファーのアドレスです。
| |**BufferHandle** |バッファーの一意の識別子が返されます。

| 戻り値 | 引数 | 説明
| ----- | ----- | ------ |
| |**NOERROR** |関数が正常に実行されました。
| |**VD_E_PROTOCOL** |仮想デバイス セットは、現在開いているではありません。
| |**VD_E_INVALID** |PBuffer が有効なアドレスではありません。
Remarks GetBufferHandle 関数を呼び出すプロセスは、データ転送が完了すると、ClientVirtualDevice::CompleteCommand を呼び出す。

## <a name="clientvirtualdevicesetmapbufferhandle"></a>ClientVirtualDeviceSet::MapBufferHandle

**目的**を他のプロセスから取得されたバッファー ハンドルから有効なバッファーのアドレスを取得するこの関数を使用します。 

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
| |**VD_E_PROTOCOL** |仮想デバイス セットは、現在開いているではありません。
| |**VD_E_INVALID** |PpBuffer は、無効なハンドルです。

**「解説」**は注意が必要、ハンドルを正常に通信します。 ハンドルは、1 つの仮想デバイスのセットに対してローカルです。 ハンドルを共有するパートナーのプロセスは、そのバッファー ハンドルを使用して、仮想デバイスのバッファーが最初に取得されたセットのスコープ内でのみを確認してください。


