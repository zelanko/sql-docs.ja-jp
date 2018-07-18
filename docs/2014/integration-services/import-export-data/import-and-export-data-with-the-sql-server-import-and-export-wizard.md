---
title: SQL Server インポートおよびエクスポート ウィザード |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 87
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 89d81ed6f880404771eb242cd0edf309be94f765
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219692"
---
# <a name="sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザード
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードを作成する最も簡単な方法を提供する[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]先のソースからデータをコピーするパッケージ。  
  
> [!NOTE]  
>  64 ビット コンピューターには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって 64 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード (DTSWizard.exe) がインストールされます。 ただし、Access や Excel など、一部のデータ ソースは、32 ビット プロバイダーでしか使用できません。 これらのデータ ソースを操作するには、32 ビット版のウィザードをインストールして実行することが必要になる場合があります。 ウィザードの 32 ビット バージョンをインストールするには、クライアント ツールを選択します。 または[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]セットアップ中にします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、[スタート] メニュー、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、またはコマンド プロンプトから起動できます。 詳細については、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザード データをコピーできますと任意のデータ ソースの間をマネージ[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]データ プロバイダーまたはネイティブ OLE DB プロバイダーは使用できます。 使用できるプロバイダーの一覧には、次のデータ ソースが含まれます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   フラット ファイル  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 ウィザードの一部の機能は、ウィザードを起動する環境に応じて動作が異なります。  
  
-   開始する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を選択して、パッケージをすぐに実行する、**をすぐに実行**チェック ボックスをオンします。 既定では、このチェック ボックスがオンになり、パッケージはすぐに実行されます。  
  
     パッケージを保存するかどうかを決定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはファイル システムにします。 パッケージを保存するように選択した場合は、パッケージの保護レベルを指定する必要もあります。 パッケージの保護レベルの詳細については、次を参照してください。[パッケージ内の機密データのアクセス制御](../security/access-control-for-sensitive-data-in-packages.md)します。  
  
     後に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードでパッケージを作成およびデータのコピーを使用することができます、[!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナーを開き、保存されたパッケージを変更するには、タスク、変換、およびイベント ドリブン ロジックを追加します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]、ウィザードによって作成されたパッケージを保存するオプションは使用できません。  
  
-   開始する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードから、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]プロジェクト[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ウィザードを完了する手順として、パッケージを実行することはできません。 代わりに、ウィザードを起動した [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトにパッケージが追加されます。 その後、パッケージを実行するか、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを使用してタスク、変換、イベント ドリブン手法を追加することにより、パッケージを拡張できます。  
  
 詳細については、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)します。  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>インポートおよびエクスポート ウィザードに必要な権限  
 完了する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードが正常にする必要があります、少なくとも次のアクセス許可。  
  
-   コピー元およびコピー先のデータベースまたはファイル共有に接続する権限。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、サーバーおよびデータベースのログイン権限が必要です。  
  
-   コピー元のデータベースまたはファイルからデータを読み取る権限。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]元のテーブルおよびビューに対する SELECT 権限が必要です。  
  
-   コピー先のデータベースまたはファイルにデータを書き込む権限。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、変換先テーブルに対する INSERT 権限が必要です。  
  
-   コピー先データベース、テーブル、またはファイルを新しく作成する場合、データベース、テーブル、またはファイルを新しく作成するための十分な権限。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE DATABASE 権限または CREATE TABLE 権限が必要です。  
  
-   Msdb データベースまたはファイル システムに書き込むための十分なアクセス許可と、ウィザードによって作成されたパッケージを保存する場合は。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、Msdb データベースに対する INSERT 権限が必要です。  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>インポートおよびエクスポート ウィザードのデータ型マッピング  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードは、最小限の変換機能を提供します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードでは、列の名前、データ型、およびデータ型プロパティを新しい変換先テーブルおよびファイルに設定できる点を除き、列レベルの変換がサポートされません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードは、マッピングを使用してファイルを[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]1 つのデータベース バージョンまたはシステムから別のデータ型をマップを提供します。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から Oracle にマップできます。 既定では、XML 形式のマッピング ファイルは、C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles にインストールされます。 既定と異なるデータ型間でのマッピングが必要であれば、マッピングの設定を変更して、ウィザードにより実行されるマッピングに適用することができます。 たとえば、する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar**データ型を DB2 にマップする**グラフィック**、DB2 ではなく、データ型**VARGRAPHIC**データ型からデータを転送するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を変更するには、DB2、 **nchar** SqlClientToIBMDB2.xml マッピング ファイルを使用でマッピング**グラフィック**の代わりに**VARGRAPHIC します。**  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、一般的に使用される変換元と変換先の多数の組み合わせ間でのマッピングが含まれています。さらに新しいマッピング ファイルを Mapping Files ディレクトリに追加して、新たな変換元と変換先をサポートすることもできます。 新しいマッピング ファイルは、公開されている XSD スキーマおよび変換元と変換先の一意の組み合わせ間でのマッピングに準拠する必要があります。  
  
> [!NOTE]  
>  終了して再起動した場合は、既存のマッピング ファイルを編集したり、フォルダーに新しいマッピング ファイルを追加したりする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードまたは[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]新しいまたは変更されたファイルが認識されるのです。  
  
## <a name="external-resources"></a>外部リソース  
  
-   ビデオ、 [Excel (SQL Server ビデオ) への SQL Server データのエクスポート](http://go.microsoft.com/fwlink/?LinkID=200975)、technet.microsoft.com  
  
-   CodePlex サンプル「[へのエクスポート ODBC からフラット ファイルを使用して、ウィザードのチュートリアル: レッスン パッケージ](http://go.microsoft.com/fwlink/?LinkId=217657)、msftisprodsamples.codeplex.com  
  
  
