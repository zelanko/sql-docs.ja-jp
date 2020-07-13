---
title: '[SQL Server のプロパティ] ([AlwaysOn 高可用性] タブ) |Microsoft Docs'
description: SQL Server 2014 で AlwaysOn 可用性グループ機能をオンまたはオフにする方法について説明します。 この機能のためにサーバーインスタンスが満たす必要のある前提条件を表示します。
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: cc145da0b6296d3f6e048905e4ab4e649294d38a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048489"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a>SQL Server のプロパティ ([AlwaysOn 高可用性] タブ)
  **構成マネージャーの** [SQL Server のプロパティ] **ダイアログ ボックスの** [AlwaysOn 高可用性] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] タブを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の AlwaysOn 可用性グループを有効または無効にします。 AlwaysOn 可用性グループの有効化は、高可用性およびディザスター リカバリー ソリューションとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが可用性グループを使用するための前提条件です。  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> 必要条件  
 AlwaysOn 可用性グループを有効にするには、サーバー インスタンスが以下の前提条件を満たしている必要があります。  
  
-   このサーバー インスタンスは、Windows Server フェールオーバー クラスタリング (WSFC) ノードに存在している必要があります。  
  
-   同じ可用性グループのインスタンスはすべて、同じ WSFC クラスターに属している必要があります。 可用性グループが複数の WSFC クラスターにまたがることはできません。  
  
-   サーバー インスタンスでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートする [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]エディションを実行する必要があります。  
  
-   一度に 1 つのサーバー インスタンスでのみ AlwaysOn 可用性グループを有効にします。 AlwaysOn 可用性グループを有効にした後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが再起動するまで待ってから、次のサーバー インスタンスを有効にしてください。  
  
> [!NOTE]  
>  サポートされている機能の詳細、および [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]の追加の前提条件、制限、推奨設定については、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] オンライン ブックをご覧ください。  
  
## <a name="dialog-options"></a>ダイアログ オプション  
 **[Windows フェールオーバー クラスター名]**  
 ローカル コンピューターのノードが含まれる WSFC クラスターの名前が表示されます。  
  
 **AlwaysOn 可用性グループの有効化**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のこのインスタンスで AlwaysOn 可用性グループを有効または無効にするには、このチェック ボックスを使用します。  
  
-   このチェック ボックスがオフの場合、AlwaysOn 可用性グループは現在無効になっています。 AlwaysOn 可用性グループを有効にするには、このチェック ボックスをオンにして、 **[OK]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを手動で再起動します。  
  
-   このチェック ボックスが既にオンに設定されている場合、AlwaysOn 可用性グループは現在有効になっています。 AlwaysOn 可用性グループを無効にするには、このチェック ボックスをオフにし、 **[OK]** をクリックします。 これにより、サーバー インスタンスが再起動します。  
  
    > [!TIP]  
    >  AlwaysOn 可用性グループを無効にした後は、サーバー インスタンスからローカル可用性レプリカをすべて削除する必要があります。 各可用性グループの最後のレプリカを削除したら、グループも削除する必要があります。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
  
> [!NOTE]  
>  AlwaysOn 可用性グループを無効にした後の設定と、可用性グループの作成および構成方法については、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] オンライン ブックを参照してください。  
  
  
