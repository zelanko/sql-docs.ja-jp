---
title: "Oracle パブリッシャー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: de65fad508e62dc2dcd09932d1a99263193f6229
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="oracle-publisher"></a>Oracle パブリッシャー
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、スナップショット レプリケーションおよびトランザクション レプリケーションを使用して、Oracle データベースからデータをパブリッシュすることができます。 詳細については、「[Oracle パブリッシングの概要](../../relational-databases/replication/non-sql/oracle-publishing-overview.md)」を参照してください。  
  
 Oracle パブリッシャーでは、リモート [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターを使用する必要があります。そのため、このウィザードは、必要な Oracle ネットワーク ソフトウェアのインストールとテストが行われた後のサーバーで実行する必要があります。 詳細については、「[Oracle パブリッシャーの構成](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)」を参照してください。  
  
> [!IMPORTANT]  
>  他の管理者が Oracle データベースをパブリッシャーとして構成している場合、 **[次へ]** をクリックすると Oracle データベースへの接続に使用されるレプリケーション ログインのパスワードを入力するよう求められます。 入力すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、ログインと Oracle データベースへのリンク サーバー接続の間のマッピングが作成されます。 以降の Oracle データベースへの接続にパスワードの入力が求められることはありません。  
  
## <a name="options"></a>オプション  
 **Oracle パブリッシャー**  
 一覧から Oracle パブリッシャーを選択します。 この一覧には、ウィザードがディストリビューターとして実行されているサーバーを使用するように、以前に構成されたことのある Oracle パブリッシャーが表示されます。 この一覧が空の場合や使用する Oracle パブリッシャーが一覧にない場合は、 **[Oracle パブリッシャーの追加]**をクリックします。  
  
 **[Oracle パブリッシャーの追加]**  
 **[ディストリビューターのプロパティ]** ダイアログ ボックスが表示されます。 このダイアログ ボックスで、 **[追加]**をクリックして、 **[Oracle パブリッシャーの追加]**をクリックします。 **[サーバーへの接続]** ダイアログ ボックスで、Oracle サーバー名およびレプリケーション管理ユーザー スキーマのログインとパスワードを指定します。 詳細については、「[[サーバーへの接続] &#40;Oracle&#41;、[ログイン]](../../relational-databases/replication/connect-to-server-oracle-login.md)」を参照してください。  
  
> [!NOTE]  
>  このウィザードが実行されているサーバーがディストリビューターとしてまだ構成されていない場合、ディストリビューターを構成するように要求されます。  
  
## <a name="see-also"></a>参照  
 [Oracle データベースからのパブリケーションの作成](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)   
 [プロパティ リファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
