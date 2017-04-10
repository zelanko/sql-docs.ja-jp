---
title: "SQL Server のプロパティ ([Always On 高可用性] タブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
caps.latest.revision: 13
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 13
---
# SQL Server のプロパティ ([Always On 高可用性] タブ)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの **[SQL Server のプロパティ]** ダイアログ ボックスの **[Always On 高可用性]** タブを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の Always On 可用性グループを有効または無効にします。 Always On 可用性グループの有効化は、高可用性および災害復旧ソリューションとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが可用性グループを使用するための前提条件です。  
  
##  <a name="Prerequisites"></a> 前提条件  
 Always On 可用性グループを有効にするには、サーバー インスタンスが以下の前提条件を満たしている必要があります。  
  
-   このサーバー インスタンスは、Windows Server フェールオーバー クラスタリング (WSFC) ノードに存在している必要があります。  
  
-   同じ可用性グループのインスタンスはすべて、同じ WSFC クラスターに属している必要があります。 可用性グループが複数の WSFC クラスターにまたがることはできません。  
  
-   サーバー インスタンスでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートする [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]エディションを実行する必要があります。  
  
-   一度に 1 つのサーバー インスタンスでのみ Always On 可用性グループを有効にします。 Always On 可用性グループを有効にした後は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが再起動するまで待ってから、次のサーバー インスタンスを有効にしてください。  
  
> [!NOTE]  
>  サポートされている機能の詳細、および [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] の追加の前提条件、制限、推奨設定については、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] オンライン ブックをご覧ください。  
  
## ダイアログ オプション  
 **[Windows フェールオーバー クラスター名]**  
 ローカル コンピューターのノードが含まれる WSFC クラスターの名前が表示されます。  
  
 **AlwaysOn 可用性グループを有効にする**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのインスタンスで Always On 可用性グループを有効または無効にするには、このチェック ボックスを使用します。  
  
-   このチェック ボックスがオフの場合、Always On 可用性グループは現在無効になっています。 Always On 可用性グループを有効にするには、このチェック ボックスをオンにして、**[OK]** をクリックし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを手動で再起動します。  
  
-   このチェック ボックスが既にオンに設定されている場合、Always On 可用性グループは現在有効になっています。 Always On 可用性グループを無効にするには、このチェック ボックスをオフにし、**[OK]** をクリックします。 これにより、サーバー インスタンスが再起動します。  
  
    > [!TIP]  
    >  Always On 可用性グループを無効にした後は、サーバー インスタンスからローカル可用性レプリカをすべて削除する必要があります。 各可用性グループの最後のレプリカを削除したら、グループも削除する必要があります。  
  
## UI 要素の一覧  
  
> [!NOTE]  
>  Always On 可用性グループを無効にした後の設定と、可用性グループの作成および構成方法については、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] オンライン ブックをご覧ください。  
  
  