---
title: "[ディストリビューターのプロパティ]、[パブリッシャー] | Microsoft Docs"
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
- sql13.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 93e8e7f09e6aa75b0ad1b9248a7a0c004695cfeb
ms.lasthandoff: 04/11/2017

---
# <a name="distributor-properties-publishers"></a>[ディストリビューターのプロパティ]、[パブリッシャー]
  **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページを使用すると、パブリッシャーでこのディストリビューターを使用できるように設定できます。 さらに、このパブリッシャーに関連付けられているプロパティも設定できます。 パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。 パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。 パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。  
  
## <a name="options"></a>オプション  
 **[ディストリビューターのプロパティ]**  
 このディストリビューターの使用を許可するサーバーを選択します。 その他のプロパティを表示し、設定するには、[パブリッシャー] の横にあるプロパティ ボタン ( **[...]** ) をクリックします。  
  
 **[追加]**  
 許可するサーバーが一覧に表示されていない場合には、 **[追加]** をクリックして、使用できるパブリッシャーの一覧に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを追加します。 追加したサーバーが、最初にこのディストリビューターをリモート ディストリビューターとして使用するサーバーである場合、管理用リンク パスワードを入力するように求められます。  
  
 **[管理用リンク パスワード]**  
 レプリケーションにより **distributor_admin** ログインを使用してパブリッシャーとリモート ディストリビューター間に作成される接続のパスワードを指定したり、更新したりできます。  
  
-   ディストリビューターがローカル ディストリビューターとしてのみ動作する場合、このパスワードはランダムに生成され、自動的に設定されます。  
  
-   既にディストリビューターにリモート パブリッシャーがある場合、パスワードはディストリビューションの構成ウィザードのこのページまたは **[ディストリビューター パスワード]** ページで最初に指定されています。  
  
-   このディストリビューターの最初のリモート パブリッシャーを有効にすると、パスワードを入力するように求められます。  
  
 ディストリビューターのセキュリティの詳細については、「[ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [パブリケーションの作成](../../relational-databases/replication/publish/create-a-publication.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
