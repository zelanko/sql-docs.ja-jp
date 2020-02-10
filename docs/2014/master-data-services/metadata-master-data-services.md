---
title: メタデータ (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2bbb98653dbbaad577f9a48d7a778b41d19fbf37
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054034"
---
# <a name="metadata-master-data-services"></a>メタデータ (マスター データ サービス)
  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] におけるユーザー定義メタデータは、モデル オブジェクトを説明するために使用する情報です。 たとえば、特定のモデルまたはエンティティの所有者を追跡する場合や、エンティティにデータを提供するソース システムを追跡する場合があります。  
  
 ユーザー定義メタデータは、**メタデータ**と呼ばれるモデルによって管理されます。 このモデルは、のインストール[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]時に自動的に含まれ、その他のすべての MDS モデルに似ています。ただし、バージョンを作成することはできません。  
  
 メタデータ モデルにユーザー定義のメタデータを投入した後は、それをサブスクリプション ビューに追加することで、サブスクライブ システムから利用できるようになります。  
  
## <a name="metadata-entities"></a>メタデータ エンティティ  
 メタデータ モデルには 5 つのエンティティが含まれます。各エンティティはユーザー定義メタデータをサポートするマスター データ モデル オブジェクトの種類を表します。 たとえば、**モデルメタデータ定義**エンティティには、モデルを表すメンバーが含まれています。また、**属性メタデータ定義**エンティティには、すべてのモデルのすべての属性を表すメンバーがあります。  
  
 モデル オブジェクトのメタデータを定義するには、こうしたメンバーのいずれかの属性を設定します。 たとえば、**エンティティメタデータ定義**エンティティでは、価格メンバーの Description 属性に、"**顧客に販売された場合の製品価格**" というテキストを入力できます。  
  
 メタデータ モデルのメンバーは、ユーザー定義メタデータをサポートするモデル オブジェクトが追加または削除されると自動的に更新されます。  
  
 メタデータ モデルでは、バージョン管理、バージョン フラグの追加または変更を行うことができません。また、メタデータ モデルをモデルの配置パッケージとして保存することもできません。 ただし、他のマスター データ モデルで使用できるその他の機能はすべて備えています。 たとえば、ビジネス ルールのセットをメタデータ モデルに実装して、データ ポリシーを強制することができます。  
  
## <a name="customizing-your-metadata-model"></a>メタデータ モデルのカスタマイズ  
 各メタデータ定義エンティティには、Name、Code、および Description の属性があります。 また、追加の属性を作成して、モデル オブジェクトを詳細に説明することができます。  
  
 たとえば、以下の属性を作成できます。  
  
-   Owner という名前のドメイン ベースの属性。各モデル オブジェクトの所有者を追跡するために使用します。  
  
-   Last Review Date という名前の自由形式の属性。所有者によってオブジェクトが最後に確認された日付を追跡するために使用します。  
  
-   ソースという名前のドメインベースの属性。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]インスタンスと対話するソースシステムを追跡および管理するために使用します。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|モデル オブジェクトにメタデータを追加します。|[メタデータの追加 &#40;マスターデータサービス&#41;](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [データのエクスポート &#40;マスターデータサービス&#41;](overview-exporting-data-master-data-services.md)  
  
  
