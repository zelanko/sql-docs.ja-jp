---
title: 管理者 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 146834648164e49632a62352d684a6da66a09e12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480016"
---
# <a name="administrators-master-data-services"></a>管理者 (Master Data Services)
  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、モデル管理者と [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者の 2 種類の管理者があります。  
  
## <a name="model-administrators"></a>モデル管理者  
 で[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]は、モデル管理者は、[**モデルオブジェクト**] タブの最上位のモデルオブジェクトに割り当てられた**更新**権限を持ち、その他の割り当てられた権限がないユーザーです。  
  
-   ユーザーに **[エクスプローラー]** 機能領域へのアクセス権がある場合、ユーザーはこのデータ領域のすべてのマスター データを追加、削除、および更新できます。  
  
-   ユーザーに他の機能領域へのアクセス権がある場合、その機能領域で利用できるすべての管理タスクを実行できます。  
  
 各モデルには複数の管理者を含めることができます。 各ユーザーは、1 つまたは複数のモデルのモデル管理者になることができ、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の配置内のすべてのモデルのモデル管理者になることもできます。  
  
 ユーザーをモデル管理者として構成するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を使用するかプログラムで構成します。 詳細については、「 [モデル管理者を作成する (マスター データ サービス)](create-a-model-administrator-master-data-services.md)」を参照してください。  
  
## <a name="master-data-services-system-administrator"></a>Master Data Services システム管理者  
 
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者は 1 人だけです。 システム管理者は、データベースの[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]作成時に**管理者アカウント**に対して指定されたユーザーです。  
  
 
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者:  
  
-   すべての機能領域に対するアクセス権が自動的に付与されます。  
  
-   [**エクスプローラー** ] 機能領域のすべてのモデルのすべてのマスターデータを追加、削除、および更新できます。  
  
  システム管理者として割り当てられているユーザーを変更できます。 詳細については、「[マスターデータサービス&#41;&#40;システム管理者アカウントを変更](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)する」を参照してください。  
  
## <a name="comparing-administrator-types"></a>管理者の種類の比較  
  
|管理者の種類|[説明]|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]システム管理者|
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] で割り当てられている権限は、管理者のアクセス権に影響を与えません。<br /><br /> すべてのモデルに対する**更新**権限が自動的に付与されます。<br /><br /> すべての機能領域に対するアクセス権が自動的に付与されます。<br /><br /> Mdm.tbluser では、 **ID**列の値は**1**です。|  
|モデル管理者|
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で割り当てられた権限によって、ユーザーがモデル管理者であるかどうかが決まります。<br /><br /> 明示的に割り当てられている権限、またはグループから継承した権限に基づいてモデル管理者になる場合があります。<br /><br /> は、最上位のモデルオブジェクトに割り当てられた**更新**権限を持ち、他の権限がないモデルに対してのみ管理者になります。<br /><br /> アクセス権が付与された機能領域だけにアクセスできます。<br /><br /> Mdm.tbluser で、 **ID**列の値が**1**ではありません。|  
  
## <a name="see-also"></a>参照  
 [モデル管理者 &#40;マスターデータサービスを作成し&#41;](create-a-model-administrator-master-data-services.md)   
 [システム管理者アカウント &#40;マスターデータサービスに変更&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [マスターデータサービスデータベースを作成する](install-windows/create-a-master-data-services-database.md)   
 [通知 &#40;マスターデータサービス&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
