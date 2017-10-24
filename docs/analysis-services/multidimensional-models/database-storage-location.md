---
title: "データベースのストレージ場所 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fb6c9aa4728cf355d0c974501fc36fd71a233a83
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="database-storage-location"></a>データベースの格納場所
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者 (DBA) が特定のデータベースをサーバー データ フォルダー以外の場所に配置することは少なくありません。 こうした状況は、パフォーマンスの向上やストレージの拡張などのビジネス上のニーズによって頻繁に発生します。 このような場合は、 **DbStorageLocation** データベース プロパティを使用すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の DBA はローカル ディスクまたはネットワーク デバイス内にデータベースの格納場所を指定できます。  
  
## <a name="dbstoragelocation-database-property"></a>DbStorageLocation データベース プロパティ  
 **DbStorageLocation** データベース プロパティでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって作成および管理されるすべてのデータベースのデータ ファイルとメタデータ ファイルのフォルダーを指定します。 メタデータ ファイルはすべて **DbStorageLocation** フォルダーに格納されますが、例外として、データベースのメタデータ ファイルはサーバー データ フォルダーに格納されます。 **DbStorageLocation** データベース プロパティの値を設定する場合は、重要な注意点が 2 つあります。  
  
-   **DbStorageLocation** データベース プロパティには、既存の UNC フォルダー パスまたは空の文字列を設定する必要があります。 空の文字列は、サーバー データ フォルダーを示す既定値です。 フォルダーが存在しない場合、 **Create**コマンド、 **Attach**コマンド、 **Alter** コマンドを実行するとエラーが発生します。  
  
-   **DbStorageLocation** データベース プロパティは、サーバー データ フォルダーまたはそのサブフォルダーを指すように設定することはできません。 サーバー データ フォルダーまたはそのサブフォルダーを指した場合、 **Create**コマンド、 **Attach**コマンド、 **Alter** コマンドを実行するとエラーが発生します。  
  
> [!IMPORTANT]  
>  固有の UNC パスを設定して、Storage Area Network (SAN)、iSCSI ベースのネットワーク、またはローカルにアタッチされたディスクを使用することをお勧めします。 ネットワーク共有への UNC パスや、待機時間の長いリモート ストレージ ソリューションは、サポートされないインストールにつながります。  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>DbStorageLocation と StorageLocation の比較  
 **DbStorageLocation** は、すべてのデータベースのデータ ファイルとメタデータ ファイルが存在するフォルダーを指定します。一方、 **StorageLocation** は、キューブのパーティションが存在するフォルダーを指定します。 **StorageLocation** は、 **DbStorageLocation**とは別に設定できます。 これは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の DBA が予想した結果に基づいて決定します。また、どちらか一方のプロパティが何度も重複して使用されます。  
  
## <a name="dbstoragelocation-usage"></a>DbStorageLocation の使用方法  
 **DbStorageLocation** データベース プロパティは、 **Detach** Attach **データベース コマンド シーケンス、**/**Backup** Restore **データベース コマンド シーケンス、**/**Synchronize** データベース コマンドの **Create** データベース コマンドの一部として使用されます。 **DbStorageLocation** データベース プロパティの変更は、データベース オブジェクトの構造の変更と見なされます。 つまり、すべてのメタデータを再作成し、データを再処理する必要があります。  
  
> [!IMPORTANT]  
>  **Alter** コマンドを使用して、データベースの格納場所を変更しないでください。 代わりに、 **Detach**/**Attach** データベース コマンド シーケンスを使用することをお勧めします (「 [Analysis Services データベースの移動](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)」および「 [Analysis Services データベースのインポートとデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)」を参照してください)。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [アタッチし、Analysis Services データベースのデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [DbStorageLocation 要素](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [要素 &#40; を作成します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)   
 [Attach 要素](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [要素 &#40; を同期します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  

