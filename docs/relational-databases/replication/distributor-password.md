---
title: ディストリビューター パスワード | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7e2a180b169a45ddd3eba1df40a3d928295a59a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616044"
---
# <a name="distributor-password"></a>[ディストリビューター パスワード]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このサーバーをリモート ディストリビューターとして使用する 1 つ以上のパブリッシャーを、このウィザードの **[パブリッシャー]** ページで有効にしている場合は、レプリケーションが **distributor_admin** ログインを使用してパブリッシャーとリモート ディストリビューターとの間で確立する接続のパスワードを指定する必要があります。 このリモート ディストリビューターを使用するそれぞれのパブリッシャーに対して、パブリケーションの新規作成ウィザードまたはディストリビューションの構成ウィザードの **[管理パスワード]** ページに、同じパスワードを入力する必要があります。 ディストリビューターのセキュリティの詳細については、「[ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)」を参照してください。  
  
## <a name="options"></a>[変数]  
 **Password**  
 パブリッシャーとリモート ディストリビューターとの間の接続に使用する複雑なパスワードを入力します。  
  
 **[パスワードの確認入力]**  
 正しく入力されたことを確認するために、パスワードを再入力します。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)   
 [パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
