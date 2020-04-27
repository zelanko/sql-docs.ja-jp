---
title: SQL Server インポートおよびエクスポートウィザード |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2f3ce90e2670357d0842b0a6ac7838f396465bab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62768167"
---
# <a name="sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザード
  インポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびエクスポートウィザードでは、変換元から変換先[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]にデータをコピーするパッケージを作成する最も簡単な方法が用意されています。  
  
> [!NOTE]  
>  64 ビット コンピューターには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって 64 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザード (DTSWizard.exe) がインストールされます。 ただし、Access や Excel など、一部のデータ ソースは、32 ビット プロバイダーでしか使用できません。 これらのデータ ソースを操作するには、32 ビット版のウィザードをインストールして実行することが必要になる場合があります。 32 ビット版のウィザードをインストールするには、セットアップ中に [クライアント ツール] または [[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]] を選択します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、[スタート] メニュー、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、またはコマンド プロンプトから起動できます。 詳細については、「 [Run the SQL Server Import And Export Wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードでは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] マネージド データ プロバイダーやネイティブ OLE DB プロバイダーを使用できる任意のデータ ソースとの間でデータをコピーできます。 使用できるプロバイダーの一覧には、次のデータ ソースが含まれます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   フラットファイル  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 ウィザードの一部の機能は、ウィザードを起動する環境に応じて動作が異なります。  
  
-   で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]インポートおよびエクスポートウィザードを起動した場合は、[**直ちに実行**する] チェックボックスをオンにするとすぐにパッケージが実行されます。 既定では、このチェック ボックスがオンになり、パッケージはすぐに実行されます。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]また、ファイルシステムにパッケージを保存するかどうかを決定することもできます。 パッケージを保存するように選択した場合は、パッケージの保護レベルを指定する必要もあります。 パッケージ保護レベルの詳細については、「[パッケージ内の機微なデータの Access Control](../security/access-control-for-sensitive-data-in-packages.md)」を参照してください。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードでパッケージを作成してデータをコピーした後、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを使用して保存したパッケージを開き、タスク、変換、イベント ドリブン ロジックを追加することでパッケージを変更できます。  
  
    > [!NOTE]  
    >  で[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]は、ウィザードによって作成されたパッケージを保存するオプションは使用できません。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトから起動する場合、ウィザードを完了する手順としてパッケージを実行することはできません。 代わりに、ウィザードを起動した [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトにパッケージが追加されます。 その後、パッケージを実行するか、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを使用してタスク、変換、イベント ドリブン手法を追加することにより、パッケージを拡張できます。  
  
 詳細については、「 [Run the SQL Server Import And Export Wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>インポートおよびエクスポート ウィザードに必要な権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを正常に完了するには、少なくとも次の権限が必要です。  
  
-   コピー元およびコピー先のデータベースまたはファイル共有に接続する権限。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、サーバーおよびデータベースへのログイン権限が必要です。  
  
-   コピー元のデータベースまたはファイルからデータを読み取る権限。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、コピー元のテーブルおよびビューに対する SELECT 権限が必要です。  
  
-   コピー先のデータベースまたはファイルにデータを書き込む権限。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、コピー先のテーブルに対する INSERT 権限が必要です。  
  
-   コピー先データベース、テーブル、またはファイルを新しく作成する場合、データベース、テーブル、またはファイルを新しく作成するための十分な権限。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE DATABASE 権限または CREATE TABLE 権限が必要です。  
  
-   ウィザードによって作成されたパッケージを保存する場合、msdb データベースまたはファイル システムに書き込むための十分な権限。 で[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]は、msdb データベースに対する INSERT 権限が必要です。  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>インポートおよびエクスポート ウィザードのデータ型マッピング  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードには、最小限の変換機能が用意されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードでは、列の名前、データ型、およびデータ型プロパティを新しい変換先テーブルおよびファイルに設定できる点を除き、列レベルの変換がサポートされません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] から提供されるマッピング ファイルを使用して、あるデータベース バージョンやシステムから、別のデータベース バージョンやシステムにデータ型をマップします。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から Oracle にマップできます。 既定では、XML 形式のマッピング ファイルは、C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles にインストールされます。 既定と異なるデータ型間でのマッピングが必要であれば、マッピングの設定を変更して、ウィザードにより実行されるマッピングに適用することができます。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] db2 にデータを転送するときに、 **nchar**データ型を db2 **vargraphic**データ型ではなく db2**グラフィック**データ型にマップするには、sqlclienttoibmdb2.xml マッピングファイルで**nchar**マッピングを変更して、vargraphic ではなく**グラフィック**を使用し**ます。**  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、一般的に使用される変換元と変換先の多数の組み合わせ間でのマッピングが含まれています。さらに新しいマッピング ファイルを Mapping Files ディレクトリに追加して、新たな変換元と変換先をサポートすることもできます。 新しいマッピング ファイルは、公開されている XSD スキーマおよび変換元と変換先の一意の組み合わせ間でのマッピングに準拠する必要があります。  
  
> [!NOTE]  
>  既存のマッピング ファイルを編集するか、新しいマッピング ファイルをフォルダーに追加する場合、新しいファイルか更新したファイルを構成するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードまたは [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を終了してから再度開く必要があります。  
  
## <a name="external-resources"></a>外部リソース  
  
-   Technet.microsoft.com のビデオ、 [Excel への SQL Server データのエクスポート (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkID=200975)  
  
-   CodePlex サンプル、[ウィザードを使用した ODBC からフラットファイルへのエクスポートチュートリアル: レッスンパッケージ](https://go.microsoft.com/fwlink/?LinkId=217657)、msftisprodsamples.codeplex.com  
  
  
