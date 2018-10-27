---
title: CA での SharePoint Web アプリに Power Pivot サービス アプリケーションを接続する |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd72f62cc513064e01c04e5a501b18a070f4c7a8
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50098975"
---
# <a name="connect-power-pivot-service-app-to-sharepoint-web-app-in-ca"></a>CA での SharePoint Web アプリに Power Pivot サービス アプリケーションを接続します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、ファーム内の任意の数の SharePoint Web アプリケーションで使用できます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを使用できるようにするには、サービス関連付けリストに PowerPivot サービス アプリケーションを追加します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードが正しく機能するには、既定のグループに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが 1 つ存在している必要があります。 既定のグループに複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを追加しないでください。 同じ型のサービス アプリケーションのエントリを複数追加する構成はサポートされていないため、エラーが発生する可能性があります。 追加のサービス アプリケーションを作成する場合は、それらをカスタム リストに追加してください。  
  
 このトピックには、次のセクションが含まれます。  
  
 [既定のグループへの PowerPivot サービス アプリケーションの追加](#default)  
  
 [カスタム サービス関連付けリストへの PowerPivot サービス アプリケーションの追加](#custom)  
  
##  <a name="default"></a> 既定のグループへのサービス アプリケーションの追加  
 サービス関連付けリストは、ファーム内の他の SharePoint Web アプリケーションにリソースを提供する共有サービスのリストです。 ファームには、サービス関連付けの既定のグループが 1 つあります。  
  
 リストに含めるには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションをアプリケーションの作成時に追加するか、アプリケーションの作成後に次の手順を使用して追加します。  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの関連付けの構成]** をクリックします。  
  
2.  アプリケーション プロキシ グループで、 **[既定]** をクリックします。  
  
3.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション (型名 **Power Pivot Service Application Proxy**で示されます) の横のチェック ボックスをオンにします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが複数ある場合は、そのうちの 1 つだけを選択します。  
  
4.  **[OK]** をクリックします。  
  
##  <a name="custom"></a> カスタム サービス関連付けリストへの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの追加  
 既定のグループは、カスタム リストで置き換えることができます。 カスタム リストは、SharePoint Web アプリケーションごとに作成します。 カスタム リストは既定のグループをオーバーライドし、既定のグループは、ファームまたはサービスの管理者が指定したサービス関連付けとのみ置き換えられます。 複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成した場合は、使用するサービス アプリケーションをカスタム リストで指定する必要があります。 カスタム リストを他の Web アプリケーションで再利用することはできません。 カスタム リストは、作成対象の Web アプリケーションにのみ適用されます。  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[Web アプリケーションの管理]** をクリックします。  
  
2.  アプリケーションを選択します ("SharePoint -80" など)。  
  
3.  Web アプリケーションの [管理] で、 **[サービス接続]** をクリックします。  
  
4.  **[次の接続グループを編集する]** で、 **[カスタム]** をクリックします。  
  
5.  使用する各サービス アプリケーション接続の横のチェック ボックスをオンにします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション ([型] が **Power Pivot Service Application Proxy**に設定されているアプリケーション) が複数ある場合は、そのうちの 1 つだけを選択してください。  
  
6.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理での Power Pivot サービス アプリケーションの作成および構成](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)   
 [初期構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)  
  
  
