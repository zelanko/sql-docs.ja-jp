---
title: "ユーザーまたはグループを削除する (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "グループの削除 [マスター データ サービス]"
  - "グループ [マスター データ サービス], 削除"
  - "ユーザー [マスター データ サービス], 削除"
  - "ユーザーの削除 [マスター データ サービス]"
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# ユーザーまたはグループを削除する (マスター データ サービス)
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスする必要のなくなったユーザーまたはグループを削除します。  
  
 ユーザーおよびグループを削除する場合、次の点に注意してください。  
  
-   ユーザーが[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]へのアクセスを持つグループのメンバーである場合、そのユーザーは、Active Directory またはローカル グループから削除されるまで[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスできます。  
  
-   グループを削除した場合、そのメンバーを削除するまで、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスしたことのあるグループのすべてのメンバーは **[ユーザー]** ボックスの一覧に表示されます。  
  
-   セキュリティの変更は、20 分間は MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] に反映されません。  
  
## 前提条件  
 この手順を実行するには  
  
-   **[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。  
  
### ユーザーまたはグループを削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]**をクリックします。  
  
2.  ユーザーを削除するには、**[ユーザー]** ページを表示します。 グループを削除するには、メニュー バーの **[グループの管理]**をクリックします。  
  
3.  グリッドで、削除するユーザーまたはグループの行を選択します。  
  
4.  **[選択したユーザーの削除]** または **[選択したグループの削除]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## 参照  
 [セキュリティ (マスター データ サービス)](../master-data-services/security-master-data-services.md)  
  
  