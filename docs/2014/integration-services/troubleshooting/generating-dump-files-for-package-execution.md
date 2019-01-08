---
title: パッケージ実行用のダンプ ファイルを生成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 61ef1731-cb3a-4afb-b4a4-059b04aeade0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00b75a698a372466dfe46d8997c730bb77ac2d1b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52799184"
---
# <a name="generating-dump-files-for-package-execution"></a>パッケージ実行用のダンプ ファイルを生成する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、パッケージの実行に関する情報を提供するデバッグ ダンプ ファイルを作成できます。 このファイル内の情報は、パッケージの実行に関する問題のトラブルシューティングに役立ちます。  
  
> [!NOTE]  
>  デバッグ ダンプ ファイルには機密情報が含まれている場合があります。 機密情報を保護するには、アクセス制御リスト (ACL) を使用してこのファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーすることができます。 たとえば、デバッグ ファイルを [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにプロジェクトを配置すると、そのプロジェクトに含まれているパッケージの実行に関する情報を提供するダンプ ファイルを作成できます。 ISServerExec.exe プロセスが終了すると、ダンプ ファイルが作成されます。 **[パッケージの実行]** ダイアログ ボックスの **[エラー時にダンプする]** オプションを選択することにより、パッケージの実行中にエラーが発生したらダンプ ファイルが作成されるように指定できます。 また、次のストアド プロシージャを使用することもできます。  
  
-   [catalog.set_execution_parameter_value (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
     パッケージの実行中にエラーまたはイベントが発生したとき、および特定のイベントが発生したときにダンプ ファイルが作成されるように構成する場合に、このストアド プロシージャを呼び出します。  
  
-   [catalog.create_execution_dump](/sql/integration-services/system-stored-procedures/catalog-create-execution-dump)  
  
     実行中のパッケージを一時停止してダンプ ファイルを作成する場合に、このストアド プロシージャを呼び出します。  
  
 パッケージ配置モデルを使用してパッケージを配置する場合は、**dtexec** ユーティリティまたは **dtutil** ユーティリティを使用して、コマンド ラインでデバッグ ダンプ オプションを指定することによって、デバッグ ダンプ ファイルを作成します。 詳細については、「 [dtexec ユーティリティ](../packages/dtexec-utility.md) 」と「 [dtutil ユーティリティ](../dtutil-utility.md)」を参照してください。 パッケージ配置モデルの詳細については、次を参照してください。 [Deployment の Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md)と[パッケージの配置&#40;SSIS&#41;](../packages/legacy-package-deployment-ssis.md)します。  
  
## <a name="debug-dump-file-format"></a>デバッグ ダンプ ファイルの形式  
 デバッグ ダンプ オプションを指定した場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって作成されるデバッグ ダンプ ファイルを次に示します。  
  
-   .mdmp デバッグ ダンプ ファイル。 これはバイナリ ファイルです。  
  
-   .tmp デバッグ ダンプ ファイル。 これはテキスト形式のファイルです。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の既定では、これらのファイルは *\<ドライブ>:* \Program Files\Microsoft SQL Server\110\Shared\ErrorDumps フォルダーに格納されます。  
  
 次の表では、.tmp ファイル内の特定のセクションのみについて説明します。 .tmp ファイルには、次の表に記載されていないデータが他にも含まれています。  
  
|情報の種類|説明|例|  
|-------------------------|-----------------|-------------|  
|環境|オペレーティング システムのバージョン、メモリの使用量のデータ、プロセス ID、およびプロセス イメージ名。 環境情報は .tmp ファイルの先頭にあります。|# SSIS Textual Dump taken at 9/13/2007 1:50:34 PM<br /><br /> #PID 4120<br /><br /> #Image Name [C:\Program Files\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]<br /><br /> # OS major=6 minor=0 build=6000<br /><br /> # Running on 2 amd64 processors under WOW64<br /><br /> # メモリ:使用中の 58% です。 物理。845 2044 M ページング:2404 4095 M/m (割当可能/合計)|  
|ダイナミック リンク ライブラリ (DLL) のパスとバージョン|パッケージの処理中にシステムによって読み込まれる各 DLL のパスとバージョン番号。|# Loaded Module: c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)<br /><br /> # 読み込まれたモジュール:C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)<br /><br /> # 読み込まれたモジュール:C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)|  
|最新のメッセージ|システムで発行された最新のメッセージ。 各メッセージの時刻、種類、説明、およびスレッド ID が含まれます。|[M:1]   Ring buffer entry:              (*pRecord)<br /><br /> [D:2]      <<\<CRingBufferLogging::RingBufferLoggingRecord>>> ( \@ 0282F1A8 )<br /><br /> [E:3]        タイムスタンプ:2007-09-13 13:50:32.786 (szTimeStamp)<br /><br /> [E:3]        スレッド ID:2368 (ThreadID)<br /><br /> [E:3]        イベント名:OnError (EventName)<br /><br /> [E:3]        ソース名:              (SourceName)<br /><br /> [E:3]        ソース ID:                      (ソース)<br /><br /> [E:3]        実行 ID:               (ExecutionGUID)<br /><br /> [E:3]         Data Code: -1073446879              (DataCode)<br /><br /> [E:3]        説明:コンポーネントが見つからないか、登録されていないか、アップグレードできないか、コンポーネントに必要なインターフェイスが見つかりません。 このコンポーネントの連絡先情報は "" です。|  
  
## <a name="related-content"></a>関連コンテンツ  
 [[パッケージの実行] ダイアログ ボックス](../execute-package-dialog-box.md)  
  
  
