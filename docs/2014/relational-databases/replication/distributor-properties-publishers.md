---
title: '[ディストリビューターのプロパティ]、[パブリッシャー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9b175c3f6385e68854effbe502fb35b775aebd9d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164303"
---
# <a name="distributor-properties-publishers"></a>[ディストリビューターのプロパティ]、[パブリッシャー]
  **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[パブリッシャー]** ページを使用すると、パブリッシャーでこのディストリビューターを使用できるように設定できます。 さらに、このパブリッシャーに関連付けられているプロパティも設定できます。 パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。 パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。 パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。  
  
## <a name="options"></a>および  
 **パブリッシャー**  
 このディストリビューターの使用を許可するサーバーを選択します。 その他のプロパティを表示し、設定するには、[パブリッシャー] の横にあるプロパティ ボタン ( **[...]** ) をクリックします。  
  
 **[追加]**  
 許可するサーバーが一覧に表示されていない場合には、 **[追加]** をクリックして、使用できるパブリッシャーの一覧に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを追加します。 追加したサーバーが、最初にこのディストリビューターをリモート ディストリビューターとして使用するサーバーである場合、管理用リンク パスワードを入力するように求められます。  
  
 **[管理用リンク パスワード]**  
 レプリケーションにより **distributor_admin** ログインを使用してパブリッシャーとリモート ディストリビューター間に作成される接続のパスワードを指定したり、更新したりできます。  
  
-   ディストリビューターがローカル ディストリビューターとしてのみ動作する場合、このパスワードはランダムに生成され、自動的に設定されます。  
  
-   既にディストリビューターにリモート パブリッシャーがある場合、パスワードはディストリビューションの構成ウィザードのこのページまたは **[ディストリビューター パスワード]** ページで最初に指定されています。  
  
-   このディストリビューターの最初のリモート パブリッシャーを有効にすると、パスワードを入力するように求められます。  
  
 ディストリビューターのセキュリティの詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](configure-distribution.md)   
 [パブリッシングとディストリビューションの構成](configure-publishing-and-distribution.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)  
  
  