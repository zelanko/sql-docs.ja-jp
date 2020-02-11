---
title: ビジネス ルールを除外する
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 30088b6964ae8120bc5aa3c1cb401ec3d9bd1149
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728167"
---
# <a name="exclude-a-business-rule-master-data-services"></a>ビジネス ルールを除外する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、ビジネス ルールを完全に削除せずにそのルールに対するデータの検証が行われないようにする場合は、ビジネス ルールを除外します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-exclude-a-business-rule"></a>ビジネス ルールを除外するには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  メニュー バーから **[管理]** をポイントして **[ビジネス ルール]** をクリックします。  
  
3.  
  **[ビジネス ルール]** ページの **[モデル]** ドロップダウン リストから、モデルを選択します。  
  
4.  
  **[エンティティ]** ドロップダウン リストから、エンティティを選択します。  
  
5.  
  **[メンバーの種類]** ドロップ ダウン リストから、メンバーの種類を選択します。  
  
6.  グリッドで、除外するビジネス ルールの行を選択し、 **[編集]** をクリックします。  
  
7.  
  **[除外]** チェック ボックスをオンにします。  
  
8.  **[保存]** をクリックします。  
  
9. 
  **[すべてパブリッシュ]** をクリックします。  
  
10. 確認のダイアログ ボックスで **[OK]** をクリックします。 
  **[ビジネス ルールの状態]** 列が **[除外]** になり、 **[除外]** 列が **[はい]** になります。  
  
## <a name="see-also"></a>参照  
 [ビジネスルール &#40;マスターデータサービスの削除&#41;](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [ビジネスルール &#40;マスターデータサービスを作成して発行&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [ビジネスルール &#40;マスターデータサービス&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
