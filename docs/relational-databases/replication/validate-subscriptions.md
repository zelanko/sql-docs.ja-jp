---
title: サブスクリプションの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8dc20dbf51f01491e5dd6bf6bb0759de0dfdb2d4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43086618"
---
# <a name="validate-subscriptions"></a>[サブスクリプションの検証]
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **[サブスクリプションの検証]** ダイアログ ボックスを使用すると、各サブスクリプションのディストリビューション エージェントを次に実行するときに、トランザクション パブリケーションに対するサブスクリプションを検証するように指定できます。 検証の結果はレプリケーション モニターに表示されます。 詳しくは、「 [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md)」をご覧ください。  
  
## <a name="options"></a>[変数]  
 **[すべての SQL Server サブスクリプションを検証する]**  
 選択すると、このパブリケーションに対するすべての SQL Server サブスクリプションのデータが検証されます。  
  
 **[以下のサブスクリプションを検証する]**  
 すべてのサブスクリプションを検証しない場合に選択します。 検証するサブスクリプションを一覧から選択します。  
  
 **[検証オプション]**  
 クリックすると、 **[サブスクリプションの検証オプション]** ダイアログ ボックスが開き、行数の検証とバイナリ チェックサムの検証のどちらを使用するかを指定できます。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  
