---
title: メタデータ (Master Data Services) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 25fa2078127816b2fd9d50bd7bd4c074c3577dae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074616"
---
# <a name="metadata-master-data-services"></a>メタデータ (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] におけるユーザー定義メタデータは、モデル オブジェクトを説明するために使用する情報です。 たとえば、特定のモデルまたはエンティティの所有者を追跡する場合や、エンティティにデータを提供するソース システムを追跡する場合があります。  
  
 ユーザー定義のメタデータがというモデルによって管理されている**メタデータ**です。 このモデルは、自動的に含まれる場合に[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]がインストールされているであり、その他のすべての MDS モデルに似ていますが、そのバージョンを作成することはできません。  
  
 メタデータ モデルにユーザー定義のメタデータを投入した後は、それをサブスクリプション ビューに追加することで、サブスクライブ システムから利用できるようになります。  
  
## <a name="metadata-entities"></a>メタデータ エンティティ  
 メタデータ モデルには 5 つのエンティティが含まれます。各エンティティはユーザー定義メタデータをサポートするマスター データ モデル オブジェクトの種類を表します。 たとえば、**モデル メタデータ定義**エンティティには、モデルを表すメンバーが含まれています、**属性メタデータ定義**エンティティがすべてのモデルのすべての属性を表すメンバー。  
  
 モデル オブジェクトのメタデータを定義するには、こうしたメンバーのいずれかの属性を設定します。 たとえば、**エンティティ メタデータ定義**エンティティ、テキスト、Price メンバーの Description 属性を設定することができます:**顧客に販売する際の製品価格**です。  
  
 メタデータ モデルのメンバーは、ユーザー定義メタデータをサポートするモデル オブジェクトが追加または削除されると自動的に更新されます。  
  
 メタデータ モデルでは、バージョン管理、バージョン フラグの追加または変更を行うことができません。また、メタデータ モデルをモデルの配置パッケージとして保存することもできません。 ただし、他のマスター データ モデルで使用できるその他の機能はすべて備えています。 たとえば、ビジネス ルールのセットをメタデータ モデルに実装して、データ ポリシーを強制することができます。  
  
## <a name="customizing-your-metadata-model"></a>メタデータ モデルのカスタマイズ  
 各メタデータ定義エンティティには、Name、Code、および Description の属性があります。 また、追加の属性を作成して、モデル オブジェクトを詳細に説明することができます。  
  
 たとえば、以下の属性を作成できます。  
  
-   Owner という名前のドメイン ベースの属性。各モデル オブジェクトの所有者を追跡するために使用します。  
  
-   Last Review Date という名前の自由形式の属性。所有者によってオブジェクトが最後に確認された日付を追跡するために使用します。  
  
-   ドメイン ベースの属性を追跡および管理と対話するソース システムを使用して、ソースを名前付き、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]インスタンス。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|モデル オブジェクトにメタデータを追加します。|[メタデータの追加&#40;マスター データ サービス&#41;](add-metadata-master-data-services.md)
)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [データのエクスポート&#40;マスター データ サービス&#41;](overview-exporting-data-master-data-services.md)  
  
  