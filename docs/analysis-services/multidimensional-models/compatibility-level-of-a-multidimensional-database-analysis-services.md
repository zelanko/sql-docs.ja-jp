---
title: "多次元データベース (Analysis Services) の互換性レベル |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 946cb28ca1e25508ac0d997c982d82886dbf4402
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="compatibility-level-of-a-multidimensional-database-analysis-services"></a>多次元データベースの互換性レベル (Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、データベース互換性レベル プロパティによって、データベースの機能レベルが決定されます。 互換性レベルは、各モデルの種類に固有です。 たとえば、互換性レベル **1100** は、データベースが多次元か表形式かによって意味が異なります。  
  
 このトピックでは、多次元データベースの互換性レベルについてのみ説明します。 表形式ソリューションの詳細については、「 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。  
  
> [!NOTE]  
>  表形式モデルには、多次元モデルに適用できないデータベース互換性レベルが存在します。 互換性レベル **1103** は、多次元モデルには存在しません。 表形式ソリューションの [1103](http://go.microsoft.com/fwlink/?LinkId=301727) の詳細については、「 **SQL Server 2012 SP1 における表形式モデルの新機能と互換性レベル** 」を参照してください。  
  
 **多次元データベースの互換性レベル**  
  
 現在、機能レベルによって異なる多次元データベースの動作は、文字列ストレージ アーキテクチャのみです。 データベースの互換性レベルを高くすることで、メジャーとディメンションの文字列ストレージの上限である 4 GB をオーバーライドできます。  
  
 多次元データベースの **CompatibilityLevel** プロパティの有効値を次に示します。  
  
|設定|Description|  
|-------------|-----------------|  
|**1050**|この値はスクリプトやツールには表示されませんが、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]で作成されたデータベースを表します。 **CompatibilityLevel** が明示的に設定されていないデータベースはすべて、暗黙的に **1050** レベルで実行されます。|  
|**1100**|これは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で作成した新しいデータベースの既定値です。 また、この値を以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成されたデータベースに指定すると、この互換性レベルでのみサポートされている機能 (つまり、文字列データを含むディメンション属性や個別のカウント メジャーの大きくなった文字列ストレージ) を使用できるようになります。<br /><br /> データベースの **CompatibilityLevel** を **1100** に設定すると、 **StringStoresCompatibilityLevel**プロパティが追加されます。このプロジェクトを使用すると、パーティションおよびディメンションの代替文字列ストレージを選択できます。|  
  
> [!WARNING]  
>  高いレベルに設定したデータベース互換性は元に戻せません。 互換性レベルを **1100**に上げた後は、データベースをより新しいサーバーで実行し続ける必要があります。 **1050**にロールバックすることはできません。 **または** より前のサーバーのバージョンでは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 1100 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]データベースをアタッチまたは復元できません。  
  
## <a name="prerequisites"></a>前提条件  
 データベース互換性レベルは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入されました。 データベース互換性レベルを表示または設定するには、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以降が必要です。  
  
 データベースをローカル キューブにすることはできません。 ローカル キューブは **CompatibilityLevel** プロパティをサポートしません。  
  
 データベースは、以前のリリース (SQL Server 2008 R2 以前) で作成され、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以降のサーバーにアタッチまたは復元されている必要があります。 SQL Server 2012 に配置されたデータベースは既に **1100** であり、ダウングレードして低いレベルで実行することはできません。  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a>多次元データベースの既存のデータベース互換性レベルの確認  
 データベース互換性レベルを表示または変更するには、XMLA を使用するしかありません。 データベースを指定する XMLA スクリプトは、SQL Server Management Studio で表示または変更できます。  
  
 データベースの XMLA 定義で **CompatibilityLevel** プロパティを検索し、それが存在しなかった場合、データベースが **1050** レベルになっている可能性が高いと考えられます。  
  
 XMLA スクリプトの表示と変更の方法については、次のセクションで説明します。  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a>SQL Server Management Studio でのデータベース互換性レベルの設定  
  
1.  互換性レベルを上げる前に、変更を元に戻すことができるように、データベースをバックアップします。  
  
2.  SQL Server Management Studio を使用して、データベースをホストする [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに接続します。  
  
3.  データベース名を右クリックし、 **[データベースをスクリプト化]**をポイントして **[ALTER]**をポイントします。次に、 **[新しいクエリ エディター ウィンドウ]**をクリックします。 データベースの XMLA 表現が新しいウィンドウで開きます。  
  
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
  
2.  別のデータベースのリンク ディメンションを使用するには、同じ互換性レベルが必要です。 たとえば、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] データベース内の [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] データベースからリンク ディメンションを使用するには、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] データベースを [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] サーバーに移植し、互換性レベルを **1100**に設定する必要があります。  
  
3.  サーバーの同期は、サーバーで同じバージョンとデータベース互換性レベルを共有している場合にのみサポートされます。  
  
## <a name="next-steps"></a>次の手順  
 データベース互換性レベルを上げると、 **で** StringStoresCompatibilityLevel [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]プロパティを設定できるようになります。 これにより、メジャーとディメンションの文字列ストレージが大きくなります。 この機能の詳細については、「 [ディメンションおよびパーティションの文字列ストレージの構成](../../analysis-services/multidimensional-models/configure-string-storage-for-dimensions-and-partitions.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベースのバックアップ、復元、および同期 &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  

