---
title: サーバーの全体管理で PowerPivot サービスアプリケーションを SharePoint Web アプリケーションに接続する |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7288979fdba0752149d8bdc6491e8c51cdebedc
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547514"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a>サーバーの全体管理で PowerPivot サービスアプリケーションを SharePoint Web アプリケーションに接続する
  PowerPivot サービス アプリケーションは、ファーム内の任意の数の SharePoint Web アプリケーションで使用できます。 PowerPivot サービス アプリケーションを使用できるようにするには、サービス関連付けリストに PowerPivot サービス アプリケーションを追加します。  
  
> [!IMPORTANT]  
>  PowerPivot 管理ダッシュボードが正しく機能するには、既定のグループに PowerPivot サービス アプリケーションが 1 つ存在している必要があります。 既定のグループに複数の PowerPivot サービス アプリケーションを追加しないでください。 同じ型のサービス アプリケーションのエントリを複数追加する構成はサポートされていないため、エラーが発生する可能性があります。 追加のサービス アプリケーションを作成する場合は、それらをカスタム リストに追加してください。  
  
 このトピックは、次のセクションで構成されています。  
  
 [既定のグループへの PowerPivot サービス アプリケーションの追加](#default)  
  
 [カスタム サービス関連付けリストへの PowerPivot サービス アプリケーションの追加](#custom)  
  
##  <a name="add-powerpivot-services-application-to-the-default-group"></a><a name="default"></a>既定のグループへの PowerPivot サービスアプリケーションの追加  
 サービス関連付けリストは、ファーム内の他の SharePoint Web アプリケーションにリソースを提供する共有サービスのリストです。 ファームには、サービス関連付けの既定のグループが 1 つあります。  
  
 リストに含めるには、PowerPivot サービス アプリケーションをアプリケーションの作成時に追加するか、アプリケーションの作成後に次の手順を使用して追加します。  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの関連付けの構成]** をクリックします。  
  
2.  アプリケーション プロキシ グループで、 **[既定]** をクリックします。  
  
3.  PowerPivot サービス アプリケーション (型名 `PowerPivot Service Application Proxy` で示されます) の横のチェック ボックスをオンにします。 PowerPivot サービス アプリケーションが複数ある場合は、そのうちの 1 つだけを選択します。  
  
4.  **[OK]** をクリックします。  
  
##  <a name="add-powerpivot-services-application-a-custom-service-association-list"></a><a name="custom"></a>カスタムサービス関連付けリストへの PowerPivot サービスアプリケーションの追加  
 既定のグループは、カスタム リストで置き換えることができます。 カスタム リストは、SharePoint Web アプリケーションごとに作成します。 カスタム リストは既定のグループをオーバーライドし、既定のグループは、ファームまたはサービスの管理者が指定したサービス関連付けとのみ置き換えられます。 複数の PowerPivot サービス アプリケーションを作成した場合は、使用するサービス アプリケーションをカスタム リストで指定する必要があります。 カスタム リストを他の Web アプリケーションで再利用することはできません。 カスタム リストは、作成対象の Web アプリケーションにのみ適用されます。  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[Web アプリケーションの管理]** をクリックします。  
  
2.  アプリケーションを選択します ("SharePoint -80" など)。  
  
3.  Web アプリケーションの [管理] で、 **[サービス接続]** をクリックします。  
  
4.  **[次の接続グループを編集する]** で、 **[カスタム]** をクリックします。  
  
5.  使用する各サービス アプリケーション接続の横のチェック ボックスをオンにします。 PowerPivot サービス アプリケーション ([型] が `PowerPivot Service Application Proxy` に設定されているアプリケーション) が複数ある場合は、そのうちの 1 つだけを選択してください。  
  
6.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理での PowerPivot サービスアプリケーションの作成と構成](create-and-configure-power-pivot-service-application-in-ca.md)   
 [初期構成 &#40;PowerPivot for SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  
