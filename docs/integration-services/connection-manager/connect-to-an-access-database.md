---
title: "Access データベースに接続する | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access [Integration Services]
- Access databases [Integration Services]
ms.assetid: 229fbd46-ef6a-4609-a4cc-d80d52c33cf1
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cbd98ef05bc8c6de066f72a9aded9243c1636f70
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-an-access-database"></a>Access データベースに接続する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを Microsoft Office Access データ ソースに接続するには、OLE DB 接続マネージャーとデータ プロパイダが必要です。 使用するデータ プロパイダは、データ ソースを作成した Access のバージョンによって異なります。  
  
-   Access 2003 以前のバージョンの場合、パッケージには [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider が必要です。  
  
-   Access 2007 の場合、パッケージには、Microsoft Office 12.0 Access データベース エンジン用の OLE DB プロバイダーが必要です。  
  
 OLE DB 接続マネージャーを作成し、対応するデータ プロパイダを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの [接続マネージャー] 領域または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードから選択することができます。  
  
> [!NOTE]  
>  64 ビット コンピューターでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access データ ソースに接続するパッケージを 32 ビット モードで実行する必要があります。 32 ビット バージョンで使用できるのは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider と Microsoft Office 12.0 Access 用の OLE DB プロバイダーだけです。  

## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Microsoft Excel および Access ファイルの接続コンポーネント
  
Microsoft Office ファイルの接続コンポーネントがまだインストールされていない場合は、必要に応じてダウンロードします。 [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)で、Access と Excel の両方のファイルの最新バージョンの接続コンポーネントをダウンロードします。
  
以前のバージョンの Access で作成したファイルは、最新バージョンのコンポーネントで開くことができます。

コンピューターに 32 ビット バージョンの Office が存在する場合は、32 ビット バージョンのコンポーネントをインストールする必要があるほか、32 ビット モードでパッケージが実行されるようにする必要があります。

Office 365 サブスクリプションがある場合は、Microsoft Access 2016 ランタイムではなく、必ず Access データベース エンジン 2016 再頒布可能パッケージをダウンロードしてください。 インストーラーを実行するときに、ダウンロードを Office のクイック実行コンポーネントとサイド バイ サイドでインストールできないことを示すエラー メッセージが表示される場合があります。 このエラー メッセージを回避するには、コマンド プロンプト ウィンドウを開き、`/quiet` スイッチを使用してダウンロードした .EXE ファイルを実行して、Quiet モードでインストールを実行します。 例:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="connecting-to-a-data-source-in-access-2003-or-earlier-format"></a>Access 2003 以前の形式のデータ ソースへの接続  
  
### <a name="to-create-an-access-connection-manager-from-the-connection-managers-area"></a>[接続マネージャー] 領域から Access 接続マネージャーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、パッケージを開きます。  
  
2.  **[接続マネージャー]** 領域内を右クリックし、 **[新しい OLE DB 接続]**を選択します。  
  
3.  **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスで、 **[新規作成]**をクリックします。  
  
     詳細については、「 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
4.  **[接続マネージャー]** ダイアログ ボックスの **[プロバイダー]**で **[Microsoft Jet 4.0 OLE DB Provider]**を選択し、接続マネージャーを適切に構成します。  
  
### <a name="to-create-an-access-connection-from-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードから Access 接続を作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。  
  
2.  **[データ ソースの選択]** ページの **[データ ソース]**で **[Microsoft Access]**を選択して、Access 接続を構成します。  
  
     **[データ ソース]** で **[Microsoft Access]**を選択すると、適切なデータ プロバイダーを使用して必要な OLE DB 接続マネージャーが自動的に作成されます。 詳細については、「 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
## <a name="connecting-to-a-data-source-in-access-2007-format"></a>Access 2007 形式のデータ ソースへの接続  
 Access 2007 データ ソースにアクセスする場合、OLE DB 接続マネージャーでは Microsoft Office 12.0 Access データベース エンジン用の OLE DB プロバイダーが必要です。 このプロバイダーは、2007 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office system と共に自動的にインストールされます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を実行しているコンピューターに 2007 Office system がインストールされていない場合は、プロバイダーを別途インストールする必要があります。 Microsoft Office 12.0 Access データベース エンジン用の OLE DB プロバイダーをインストールするには、「 [2007 Office System ドライバー : データ接続コンポーネント](http://go.microsoft.com/fwlink/?LinkId=98155)」でコンポーネントをダウンロードしてインストールしてください。  
  
### <a name="to-create-an-ole-db-connection-manager-from-the-connection-managers-area"></a>[接続マネージャー] 領域から OLE DB 接続マネージャーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、パッケージを開きます。  
  
2.  **[接続マネージャー]** 領域内を右クリックし、 **[新しい OLE DB 接続]**を選択します。  
  
3.  **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスで、 **[新規作成]**をクリックします。  
  
     詳細については、「 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
4.  **[接続マネージャー]** ダイアログ ボックスの **[プロバイダー]**で **[Microsoft Office 12.0 Access Database Engine OLE DB]**を選択し、接続マネージャーを適切に構成します。  
  
    > [!NOTE]  
    >  Access 2007 を使用するデータ ソースに接続する場合は、 **[データ ソース]** で **[Microsoft Jet 4.0 OLE DB Provider]**を選択することはできません。  
  
### <a name="to-create-an-ole-db-connection-from-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードから OLE DB 接続を作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを起動します。  
  
2.  **[データ ソースの選択]** ページの **[データ ソース]**で **[Microsoft Office 12.0 Access Database Engine OLE DB Provider]**を選択し、接続マネージャーを適切に構成します。  
  
    > [!NOTE]  
    >  Access 2007 を使用するデータ ソースに接続する場合は、 **[データ ソース]** で **[Microsoft Jet 4.0 OLE DB Provider]**を選択することはできません。  
  
     **[データ ソース]** で **[Microsoft Office 12.0 Access Database Engine OLE DB Provider]**を選択すると、適切なデータ プロバイダーを使用して必要な OLE DB 接続マネージャーが自動的に作成されます。 詳細については、「 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  
