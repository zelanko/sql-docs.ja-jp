---
title: ファイル属性を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating file attributes [Master Data Services]
- attributes [Master Data Services], creating file attributes
ms.assetid: d224886b-2ef1-4658-8b01-2213cc4b8df6
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 387613e12af3435a2a8eb9e3f630f61acaf28a8d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479991"
---
# <a name="create-a-file-attribute-master-data-services"></a>ファイル属性を作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でファイル属性を作成して、ファイルで属性値を設定します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。  
  
-   属性を作成するエンティティが存在する必要があります。 詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。  
  
### <a name="to-create-a-file-attribute"></a>ファイル属性を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。  
  
3.  **[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  属性を作成するエンティティの行を選択します。  
  
5.  **[選択したエンティティの編集]** をクリックします。  
  
6.  **[エンティティの編集]** ページで、次の手順を実行します。  
  
    -   リーフ メンバーの属性の場合は、 **[リーフ メンバー属性]** ペインで **[リーフ属性の追加]** をクリックします。  
  
    -   統合メンバーの属性の場合は、 **[統合メンバー属性]** ペインで **[統合属性の追加]** をクリックします。  
  
    -   コレクションの属性の場合は、 **[コレクション属性]** ペインで **[コレクション属性の追加]** をクリックします。  
  
7.  [**属性の追加**] ページで、[**ファイル**] オプションを選択します。  
  
8.  **[名前]** ボックスに属性の名前を入力します。 属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)」を参照してください。  
  
9. **[ピクセル幅の表示]** ボックスに、 **[エクスプローラー]** グリッドに表示する属性列の幅を入力します。  
  
10. [**ファイル拡張子**] ボックスの一覧で、ユーザーがアップロードできるファイルの種類を1つ以上選択するか、既定\*値 (*.) のままにしてすべてのファイルの種類を許可します。  
  
11. 必要に応じて、 **[変更の追跡を有効化]** を選択して、属性のグループに対する変更を追跡します。 詳細については、「[変更の追跡グループに属性を追加する方法 (マスター データ サービス)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)」を参照してください。  
  
12. **[属性の保存]** をクリックします。  
  
13. **[エンティティのメンテナンス]** ページで **[エンティティの保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性 &#40;マスターデータサービス&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [属性名を変更する &#40;マスターデータサービス&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [ドメインベースの属性 &#40;マスターデータサービスを作成&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [テキスト属性を作成する (マスター データ サービス)](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
  
