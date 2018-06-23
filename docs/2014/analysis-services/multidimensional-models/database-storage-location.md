---
title: データベースのストレージ場所 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1b7c62d96993f1103a216e378bdf89d7b1cdf4ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178759"
---
# <a name="database-storage-location"></a>データベースの格納場所
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者 (DBA) が特定のデータベースをサーバー データ フォルダー以外の場所に配置することは少なくありません。 こうした状況は、パフォーマンスの向上やストレージの拡張などのビジネス上のニーズによって頻繁に発生します。 このような場合は、`DbStorageLocation` データベース プロパティを使用すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の DBA はローカル ディスクまたはネットワーク デバイス内にデータベースの格納場所を指定できます。  
  
## <a name="dbstoragelocation-database-property"></a>DbStorageLocation データベース プロパティ  
 `DbStorageLocation`データベース プロパティは、フォルダーを指定場所[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を作成し、すべてのデータベース データとメタデータ ファイルを管理します。 すべてのメタデータ ファイルが格納されている、`DbStorageLocation`例外として、サーバー データ フォルダーに格納されているデータベースのメタデータ ファイルのフォルダーです。 値を設定するときに 2 つの重要な考慮事項がある`DbStorageLocation`データベースのプロパティ。  
  
-   `DbStorageLocation`データベース プロパティは、既存の UNC フォルダー パスまたは空の文字列に設定する必要があります。 空の文字列は、サーバー データ フォルダーを示す既定値です。 実行するときに、エラーが発生する、フォルダーが存在しない場合、 `Create`、 `Attach`、または`Alter`コマンド。  
  
-   `DbStorageLocation`サーバー データ フォルダーまたはサブフォルダーのいずれかを指すデータベース プロパティを設定することはできません。 実行するときに、エラーが発生する場所は、サーバー データ フォルダーまたはサブフォルダーのいずれかをポイントしている場合、 `Create`、 `Attach`、または`Alter`コマンド。  
  
> [!IMPORTANT]  
>  固有の UNC パスを設定して、Storage Area Network (SAN)、iSCSI ベースのネットワーク、またはローカルにアタッチされたディスクを使用することをお勧めします。 ネットワーク共有への UNC パスや、待機時間の長いリモート ストレージ ソリューションは、サポートされないインストールにつながります。  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>DbStorageLocation と StorageLocation の比較  
 `DbStorageLocation` は、すべてのデータベースのデータ ファイルとメタデータ ファイルが存在するフォルダーを指定します。一方、`StorageLocation` は、キューブのパーティションが存在するフォルダーを指定します。 `StorageLocation` は、`DbStorageLocation` とは別に設定できます。 これは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の DBA が予想した結果に基づいて決定します。また、どちらか一方のプロパティが何度も重複して使用されます。  
  
## <a name="dbstoragelocation-usage"></a>DbStorageLocation の使用方法  
 `DbStorageLocation`データベース プロパティの一部として使用する`Create`データベース コマンド、 `Detach` / `Attach`データベース コマンド シーケンス、 `Backup` / `Restore`データベース コマンド シーケンス、または、`Synchronize`データベース コマンド。 `DbStorageLocation` データベース プロパティの変更は、データベース オブジェクトの構造の変更と見なされます。 つまり、すべてのメタデータを再作成し、データを再処理する必要があります。  
  
> [!IMPORTANT]  
>  `Alter` コマンドを使用して、データベースの格納場所を変更しないでください。 代わりに、推奨のシーケンスを使用して`Detach` / `Attach`データベース コマンド (を参照してください[Analysis Services データベースを移動](move-an-analysis-services-database.md)、[アタッチおよびデタッチ Analysis Services データベース](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [アタッチし、Analysis Services データベースのデタッチ](attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](move-an-analysis-services-database.md)   
 [DbStorageLocation 要素](../xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [要素を作成する&#40;XMLA&#41;](../xmla/xml-elements-commands/create-element-xmla.md)   
 [Attach 要素](../xmla/xml-elements-commands/attach-element.md)   
 [Synchronize 要素&#40;XMLA&#41;](../xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  