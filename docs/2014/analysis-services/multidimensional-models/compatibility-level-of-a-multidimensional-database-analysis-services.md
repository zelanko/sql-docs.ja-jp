---
title: 多次元データベースの互換性レベルの設定 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5edbd0ab8f713d227e4ef06307090b6079390869
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537134"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a>多次元データベースの互換性レベルの設定 (Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、データベース互換性レベル プロパティによって、データベースの機能レベルが決定されます。 互換性レベルは、各モデルの種類に固有です。 たとえば、の互換性レベルは、 `1100` データベースが多次元か表形式かによって異なる意味を持ちます。  
  
 このトピックでは、多次元データベースの互換性レベルについてのみ説明します。 表形式ソリューションの詳細については、「[互換性レベル &#40;SSAS 表形式 SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。  
  
> [!NOTE]  
>  表形式モデルには、多次元モデルに適用できないデータベース互換性レベルが存在します。 互換性レベル `1103` は、多次元モデルには存在しません。 表形式ソリューションの詳細について[は、SQL Server 2012 SP1 および互換性レベルの表形式モデルの新機能](https://go.microsoft.com/fwlink/?LinkId=301727)を参照してください `1103` 。  
  
 **多次元データベースの互換性レベル**  
  
 現在、機能レベルによって異なる多次元データベースの動作は、文字列ストレージ アーキテクチャのみです。 データベースの互換性レベルを高くすることで、メジャーとディメンションの文字列ストレージの上限である 4 GB をオーバーライドできます。  
  
 多次元データベースの `CompatibilityLevel` プロパティの有効値を以下に示します。  
  
|設定|説明|  
|-------------|-----------------|  
|`1050`|この値はスクリプトやツールには表示されませんが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]で作成されたデータベースを表します。 `CompatibilityLevel` が明示的に設定されていないデータベースはすべて、暗黙的に `1050` レベルで実行されます。|  
|`1100`|これは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で作成した新しいデータベースの既定値です。 また、この値を以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースに指定すると、この互換性レベルでのみサポートされている機能 (つまり、文字列データを含むディメンション属性や個別のカウント メジャーの大きくなった文字列ストレージ) を使用できるようになります。<br /><br /> データベースには、 `CompatibilityLevel` 追加のプロパティが設定されてい `1100` `StringStoresCompatibilityLevel` ます。これにより、パーティションおよびディメンションの代替文字列ストレージを選択できます。|  
  
> [!WARNING]  
>  高いレベルに設定したデータベース互換性は元に戻せません。 互換性レベルをに上げた後は `1100` 、データベースを新しいサーバーで実行し続ける必要があります。 にロールバックすることはできません `1050` 。 `1100`またはより前のサーバーのバージョンでは、データベースをアタッチまたは復元することはできません [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。  
  
## <a name="prerequisites"></a>前提条件  
 データベース互換性レベルは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入されました。 データベース互換性レベルを表示または設定するには、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以降が必要です。  
  
 データベースをローカル キューブにすることはできません。 ローカル キューブでは、`CompatibilityLevel` プロパティがサポートされません。  
  
 データベースは、以前のリリース (SQL Server 2008 R2 以前) で作成され、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以降のサーバーにアタッチまたは復元されている必要があります。 SQL Server 2012 に配置されたデータベースは既に `1100` であり、ダウングレードして低いレベルで実行することはできません。  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a>多次元データベースの既存のデータベース互換性レベルの確認  
 データベース互換性レベルを表示または変更するには、XMLA を使用するしかありません。 データベースを指定する XMLA スクリプトは、SQL Server Management Studio で表示または変更できます。  
  
 データベースの XMLA 定義で `CompatibilityLevel` プロパティを検索し、それが存在しなかった場合、データベースが `1050` レベルになっている可能性が高いと考えられます。  
  
 XMLA スクリプトの表示と変更の方法については、次のセクションで説明します。  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a>SQL Server Management Studio でのデータベース互換性レベルの設定  
  
1.  互換性レベルを上げる前に、変更を元に戻すことができるように、データベースをバックアップします。  
  
2.  SQL Server Management Studio を使用して、データベースをホストする [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに接続します。  
  
3.  データベース名を右クリックし、 **[データベースをスクリプト化]** をポイントして **[ALTER]** をポイントします。次に、 **[新しいクエリ エディター ウィンドウ]** をクリックします。 データベースの XMLA 表現が新しいウィンドウで開きます。  
  
4.  次の XML 要素をコピーします。  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  それを、 `</Annotations>` 終了要素の後、 `<Language>` 要素の前に貼り付けます。 XML は次の例のようになります。  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  ファイルを保存します。  
  
7.  スクリプトを実行するには、[クエリ] メニューの **[実行]** をクリックするか、F5 キーを押します。  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a>同じ互換性レベルが必要なサポートされる操作  
 次の操作では、ソース データベースで同じ互換性レベルを共有している必要があります。  
  
1.  異なるデータベースのパーティションのマージは、両方のデータベースで同じ互換性レベルを共有している場合にのみサポートされます。  
  
2.  別のデータベースのリンク ディメンションを使用するには、同じ互換性レベルが必要です。 たとえば、データベースのデータベースからリンクディメンションを使用する場合は、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] データベースを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] サーバーに移植 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] し、互換性レベルをに設定する必要があり `1100` ます。  
  
3.  サーバーの同期は、サーバーで同じバージョンとデータベース互換性レベルを共有している場合にのみサポートされます。  
  
## <a name="next-steps"></a>次の手順  
 データベース互換性レベルを上げると、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で `StringStoresCompatibilityLevel` プロパティを設定できるようになります。 これにより、メジャーとディメンションの文字列ストレージが大きくなります。 この機能の詳細については、「 [ディメンションおよびパーティションの文字列ストレージの構成](configure-string-storage-for-dimensions-and-partitions.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベースのバックアップ、復元、および同期 &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
