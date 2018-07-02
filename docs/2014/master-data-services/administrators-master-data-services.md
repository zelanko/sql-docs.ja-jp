---
title: 管理者 (Master Data Services) | Microsoft Docs
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
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 11abfb4949bdd7917066ed785dd1014efc026e9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076250"
---
# <a name="administrators-master-data-services"></a>管理者 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、モデル管理者と [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者の 2 種類の管理者があります。  
  
## <a name="model-administrators"></a>モデル管理者  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]、モデル管理者を持つユーザーは、**更新**で最上位のモデル オブジェクトに割り当てられている権限、**モデル オブジェクト**] タブおよびないその他のアクセス許可を割り当てます。  
  
-   ユーザーに **[エクスプローラー]** 機能領域へのアクセス権がある場合、ユーザーはこのデータ領域のすべてのマスター データを追加、削除、および更新できます。  
  
-   ユーザーに他の機能領域へのアクセス権がある場合、その機能領域で利用できるすべての管理タスクを実行できます。  
  
 各モデルには複数の管理者を含めることができます。 各ユーザーは、1 つまたは複数のモデルのモデル管理者になることができ、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の配置内のすべてのモデルのモデル管理者になることもできます。  
  
 ユーザーをモデル管理者として構成するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を使用するかプログラムで構成します。 詳細については、「[モデル管理者を作成する (マスター データ サービス)](create-a-model-administrator-master-data-services.md)」を参照してください。  
  
## <a name="master-data-services-system-administrator"></a>Master Data Services システム管理者  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者は 1 人だけです。 システム管理者は、指定されたユーザー、**管理者アカウント**を作成するとき、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]データベース。  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者:  
  
-   すべての機能領域に対するアクセス権が自動的に付与されます。  
  
-   追加、削除、およびすべてのモデルのすべてのマスター データを更新することができます、**エクスプ ローラー**機能領域。  
  
 システム管理者として割り当てられているユーザーを変更できます。 詳細については、次を参照してください。[システム管理者アカウントを変更&#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)です。  
  
## <a name="comparing-administrator-types"></a>管理者の種類の比較  
  
|管理者の種類|説明|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] で割り当てられている権限は、管理者のアクセス権に影響を与えません。<br /><br /> 自動的に**更新**すべてのモデルにアクセスを許可します。<br /><br /> すべての機能領域に対するアクセス権が自動的に付与されます。<br /><br /> Mdm.tbluser の値、 **ID**列は**1**です。|  
|モデル管理者|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で割り当てられた権限によって、ユーザーがモデル管理者であるかどうかが決まります。<br /><br /> 明示的に割り当てられている権限、またはグループから継承した権限に基づいてモデル管理者になる場合があります。<br /><br /> モデルに対してのみ管理者**更新**最上位のモデル オブジェクトに割り当てられた権限とアクセス権なし。<br /><br /> アクセス権が付与された機能領域だけにアクセスできます。<br /><br /> Mdm.tbluser の値、 **ID**列がない**1**です。|  
  
## <a name="see-also"></a>参照  
 [モデル管理者を作成する&#40;マスター データ サービス&#41;](create-a-model-administrator-master-data-services.md)   
 [システム管理者アカウントを変更&#40;マスター データ サービス&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [マスター データ サービス データベースの作成](install-windows/create-a-master-data-services-database.md)   
 [通知&#40;マスター データ サービス&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  