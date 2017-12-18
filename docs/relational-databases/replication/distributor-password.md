---
title: "ディストリビューター パスワード | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0104061da4cf79f6b031f0a0d3af736e924eacbf
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="distributor-password"></a>[ディストリビューター パスワード]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このサーバーをリモート ディストリビューターとして使用する 1 つ以上のパブリッシャーを、このウィザードの **[パブリッシャー]** ページで有効にしている場合は、レプリケーションが **distributor_admin** ログインを使用してパブリッシャーとリモート ディストリビューターとの間で確立する接続のパスワードを指定する必要があります。 このリモート ディストリビューターを使用するそれぞれのパブリッシャーに対して、パブリケーションの新規作成ウィザードまたはディストリビューションの構成ウィザードの **[管理パスワード]** ページに、同じパスワードを入力する必要があります。 ディストリビューターのセキュリティの詳細については、「[ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **Password**  
 パブリッシャーとリモート ディストリビューターとの間の接続に使用する複雑なパスワードを入力します。  
  
 **[パスワードの確認入力]**  
 正しく入力されたことを確認するために、パスワードを再入力します。  
  
## <a name="see-also"></a>参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
