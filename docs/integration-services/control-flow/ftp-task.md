---
title: "FTP タスク | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftptask.f1"
helpviewer_keywords: 
  - "FTP タスク [Integration Services]"
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
caps.latest.revision: 52
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 52
---
# FTP タスク
  FTP タスクは、データ ファイルをダウンロードまたはアップロードし、サーバー上のディレクトリを管理します。 たとえば、パッケージは、リモート サーバーまたはインターネット サイトから、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ ワークフローの一部としてデータ ファイルをダウンロードできます。 FTP タスクは、次の目的で使用できます。  
  
-   データを移動し、変換をデータに適用する前または後で、あるディレクトリから別のディレクトリに、ディレクトリやデータ ファイルをコピーします。  
  
-   コピー元の FTP サイトにログインし、ファイルやパッケージをコピー先のディレクトリにコピーします。  
  
-   データをデータベースに読み込む前に、FTP サイトからファイルをダウンロードし、変換を列データに適用します。  
  
 実行時には、FTP タスクは FTP 接続マネージャーを使用してサーバーに接続します。 FTP 接続マネージャーは、FTP タスクとは別に構成され、FTP タスク内で参照されます。 FTP 接続マネージャーには、サーバーの設定、FTP サーバーへのアクセス資格情報、および、サーバーへの接続のタイムアウトや再試行回数などのオプションが含まれています。 詳細については、「[FTP 接続マネージャー](../../integration-services/connection-manager/ftp-connection-manager.md)」を参照してください。  
  
> [!IMPORTANT]  
>  FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 ローカル ファイルまたはローカル ディレクトリにアクセスする場合、FTP タスクは、ファイル接続マネージャー、または変数に格納されたパス情報を使用します。 それに対し、リモート ファイルまたはリモート ディレクトリにアクセスする場合、FTP タスクは、FTP 接続マネージャーで直接指定されたリモート サーバーのパス、または変数に格納されたパス情報を使用します。 詳細については、「[ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)」および「[Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)」を参照してください。  
  
 したがって、FTP タスクは複数のファイルを受信し、複数のリモート ファイルを削除できます。ただし、FTP タスクが接続マネージャーを使用している場合には、1 つのファイルのみを送信し、1 つのローカル ファイルのみを削除できます。ファイル接続マネージャーがアクセスできるのは 1 ファイルのみであるためです。 複数のローカル ファイルにアクセスするには、FTP タスクで変数を使用してパス情報を指定する必要があります。 たとえば、"C:\Test\\*.txt" を含む変数は、Test ディレクトリ内で .txt 拡張子を持つすべてのファイルの削除または送信をサポートするパスを提供します。  
  
 複数のファイルを送信したり、複数のローカル ファイルまたはディレクトリにアクセスするには、Foreach ループに FTP タスクを含めて、複数回実行する方法もあります。 Foreach ループは、For Each File 列挙子を使用して、ディレクトリ内のファイル全体を列挙します。 詳細については、「[Foreach ループ コンテナー](../../integration-services/control-flow/foreach-loop-container.md)」を参照してください。  
  
 FTP タスクでは、パス内で *?* および *\** ワイルドカード文字がサポートされます。 これによってタスクは複数のファイルにアクセスできます。 ただし、ワイルドカードが使用できるのは、パスのファイル名を指定する部分のみです。 たとえば、C:\MyDirectory\\*.txt は有効なパスですが、C:\\\*\MyText.txt は無効なパスです。  
  
 操作に失敗した場合にファイル システムに関するタスクを停止したり、ファイルを ASCII モードで転送するように FTP 操作を構成できます。 ファイルのコピーを送受信する操作は、コピー先のファイルおよびディレクトリを上書きするように構成できます。  
  
## 定義済みの FTP 操作  
 FTP タスクには、定義済みの操作のセットが含まれています。 次の表では、これらの操作について説明します。  
  
|操作|Description|  
|---------------|-----------------|  
|ファイルの送信|ローカル コンピューターのファイルを FTP サーバーに送信します。|  
|ファイルの受信|FTP サーバーのファイルをローカル コンピューターに保存します。|  
|ローカル ディレクトリの作成|ローカル コンピューター上にフォルダーを作成します。|  
|リモート ディレクトリの作成|FTP サーバー上にフォルダーを作成します。|  
|ローカル ディレクトリの削除|ローカル コンピューター上のフォルダーを削除します。|  
|リモート ディレクトリの削除|FTP サーバー上のフォルダーを削除します。|  
|ローカル ファイルの削除|ローカル コンピューターのファイルを削除します。|  
|リモート ファイルの削除|FTP サーバーのファイルを削除します。|  
  
## FTP タスクで使用できるカスタム ログ エントリ  
 次の表は、FTP タスクのカスタム ログ エントリの一覧です。 詳細については、「[Integration Services (SSIS) のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../../integration-services/performance/custom-messages-for-logging.md)」を参照してください。  
  
|ログ エントリ|Description|  
|---------------|-----------------|  
|**FTPConnectingToServer**|タスクで FTP サーバーへの接続が開始されたことを示します。|  
|**FTPOperation**|タスクで実行された FTP 操作の開始および種類を報告します。|  
  
## 関連タスク  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 これらのプロパティを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「[タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)」を参照してください。  
  
 プログラムによってこれらのプロパティを設定する方法の詳細については、「<xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>」を参照してください。  
  
## 参照  
 [[FTP タスク エディター] ([全般] ページ)](../Topic/FTP%20Task%20Editor%20\(General%20Page\).md)   
 [FTP タスク エディター ([ファイル転送] ページ)](../Topic/FTP%20Task%20Editor%20\(File%20Transfer%20Page\).md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  