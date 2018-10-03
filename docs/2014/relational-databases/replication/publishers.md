---
title: パブリッシャー | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df92a2632047ae23c15973806848ac824f982818
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096492"
---
# <a name="publishers"></a>[ディストリビューターのプロパティ]
  他のパブリッシャーにこのディストリビューターの使用許可を与えることができます。 パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。 パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。 パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。  
  
 パブリッシャーとして選択したサーバーでは、このウィザードの **[ディストリビューション データベース]** ページで指定したディストリビューション データベースが使用されます。 他のディストリビューション データベースを使用する場合には、この時点でパブリッシャーを有効にしないでください。 代わりに、ディストリビューションの構成ウィザードの終了後に、 **[ディストリビューターのプロパティ]** ダイアログ ボックスを使用してパブリッシャーを追加します。  
  
## <a name="options"></a>および  
 **パブリッシャー**  
 このディストリビューターの使用を許可するサーバーを選択します。 その他のプロパティを表示し、設定するには、[パブリッシャー] の横にあるプロパティ ボタン (**[...]**) をクリックします。  
  
 **[追加]**  
 許可するサーバーが一覧に表示されていない場合には、 **[追加]** をクリックして、使用できるパブリッシャーの一覧に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを追加します。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](configure-distribution.md)   
 [パブリッシングとディストリビューションの構成](configure-publishing-and-distribution.md)   
 [View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md)   
 [Publisher で文書を作成するには](publish/create-a-publication.md)  
  
  
