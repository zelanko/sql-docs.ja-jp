---
title: サブスクリプションビューを作成する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c4a2f747192b1cddefeac256d4470a2b345305de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479950"
---
# <a name="create-a-subscription-view-master-data-services"></a>サブスクリプション ビューを作成する (マスター データ サービス)
  サブスクライブシステムで使用するために[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]データベースにデータのビューを作成する場合は、サブスクリプションビューを作成します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   
  **[統合管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-create-a-subscription-view"></a>サブスクリプション ビューを作成するには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[統合管理]** をクリックします。  
  
2.  メニュー バーの **[ビューの作成]** をクリックします。  
  
3.  [**サブスクリプションビュー** ] ページで、[**サブスクリプションビューの追加**] をクリックします。  
  
4.  [**サブスクリプションビューの作成**] ペインで、[**サブスクリプションビュー名**] ボックスにビューの名前を入力します。  
  
5.  
  **[モデル]** ボックスの一覧からモデルを選択します。  
  
6.  [**バージョン**] または [**バージョンフラグ**] のいずれかのオプションを選択し、対応する一覧から選択します。  
  
    > [!TIP]  
    >  サブスクリプション ビューはバージョン フラグに基づいて作成します。 バージョンをロックするとき、サブスクリプション ビューを更新せずに未処理のバージョンにフラグを割り当て直すことができます。  
  
7.  [**エンティティ**] または [**派生階層**] のいずれかのオプションを選択し、対応する一覧から選択します。  
  
8.  
  **[形式]** ボックスの一覧からサブスクリプション ビュー形式を選択します。  
  
9. 
  **[形式]** ボックスの一覧から **[明示的レベル]** または **[派生レベル]** を選択した場合、ビューに含める階層内のレベル数を入力します。  
  
10. **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [データのエクスポート &#40;マスターデータサービス&#41;](overview-exporting-data-master-data-services.md)   
 [サブスクリプションビュー &#40;マスターデータサービスの削除&#41;](delete-a-subscription-view-master-data-services.md)   
 [バージョンフラグ &#40;マスターデータサービスを作成し&#41;](create-a-version-flag-master-data-services.md)  
  
  
