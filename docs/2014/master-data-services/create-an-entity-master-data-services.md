---
title: エンティティを作成する (マスター データ サービス) | Microsoft Docs
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
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 23e267d78091895e5d0ec899835ce7aa09e8c9d3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072121"
---
# <a name="create-an-entity-master-data-services"></a>エンティティを作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でエンティティを作成して、メンバーおよびその属性を含めます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
-   モデルが存在する必要があります。 詳細については、「[モデルを作成する (マスター データ サービス)](../../2014/master-data-services/create-a-model-master-data-services.md)」を参照してください。  
  
### <a name="to-create-an-entity"></a>エンティティを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。  
  
3.  **[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  をクリックして**エンティティを追加**です。  
  
5.  **エンティティ名**ボックスに、エンティティの名前を入力します。  
  
6.  **ステージング テーブルの名前**ボックスで、ステージング テーブルの名前を入力します。  
  
    > [!TIP]  
    >  ステージング テーブルの名前の一部にはモデル名を使用します。たとえば、 *Modelname_Entityname*のようにします。 こうすることで、データベースからテーブルを見つけやすくなります。 ステージング テーブルの詳細については、次を参照してください。[データのインポート&#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)です。  
  
7.  任意。 **[コード値を自動的に作成する]** チェック ボックスをオンにします。 詳細については、「[コードの自動作成 (マスター データ サービス)](../../2014/master-data-services/automatic-code-creation-master-data-services.md)」を参照してください。  
  
8.  **明示的階層およびコレクションを有効にする**一覧で、次のオプションのいずれかを選択します。  
  
    -   **いいえ**です。 明示的階層およびコレクションに対してエンティティを有効にする必要がない場合、このオプションを選択します。 これは、必要に応じて後で変更できます。  
  
    -   **[はい]** です。 明示的階層およびコレクションに対してエンティティを有効にする場合、このオプションを選択します。 **明示的階層名**ボックスで、名前を入力します。 必要に応じて、選択**必須階層 (すべてのリーフ メンバーが含まれる**して、明示的階層を必須階層にします。  
  
9. をクリックして**エンティティの保存**です。  
  
## <a name="next-steps"></a>次の手順  
  
-   [テキスト属性を作成する&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [ドメイン ベースの属性を作成する&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [ファイル属性を作成する&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [エンティティ&#40;マスター データ サービス&#41;](../../2014/master-data-services/entities-master-data-services.md)   
 [明示的階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [エンティティ名を変更&#40;マスター データ サービス&#41;](edit-an-entity-master-data-services.md)   
 [エンティティを削除する&#40;マスター データ サービス&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  