---
title: "SQL Server Integration Services のプロパティ (サービス タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
caps.latest.revision: "16"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 01411079b539ebc1629ac39596f6c34d7f2c65f3
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-integration-services-properties-service-tab"></a>[SQL Server Integration Services のプロパティ] ダイアログ ボックス ([サービス] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用して、**サービス**タブで、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **プロパティ** ダイアログ ボックスを表示または、次のオプションを指定します。  
  
## <a name="options"></a>オプション  
 **[バイナリ パス]**  
 このサービスが使用するプログラム ファイルの場所が表示されます。  
  
 **[エラー制御]**  
 1 は `SERVICE_ERROR_NORMAL`を示します。 コンピューターの起動時にこのサービスが開始しなかった場合は、スタートアップ プログラムによってログにエラーが記録され、ポップアップ メッセージ ボックスが表示されますが、スタートアップ操作は継続します。 この値は変更できません。  
  
 **終了コード**  
 このサービスの開始時または停止時に検出された問題を定義する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows エラー コードです。 このクラスで表されるサービスに固有のエラーが検出されると、このプロパティは **ERROR_SERVICE_SPECIFIC_ERROR** (1066) に設定され、そのエラーに関する情報は、 **ServiceSpecificExitCode** プロパティで利用できるようになります。 この値は、実行中と正常終了時には NO_ERROR (0) に設定されます。  
  
 **Host Name**  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] サービスを実行しているコンピューターまたはクラスターの名前が表示されます。  
  
 **名前**  
 サービスの表示名が表示されます。  
  
 **プロセス ID**  
 Windows プロセス ID が表示されます。  
  
 **[SQL サービスの種類]**  
 呼び出し側プロセスに提供されるサービスの種類が表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いくつかのサービスをインストールします。  
  
 **[開始モード]**  
 このサービスを以下のいずれかのモードに設定します。  
  
-   「手動」: このサービスは、コンピューターの起動時に自動的に開始しません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは他のツールを使用してこのサービスを開始する必要があります。  
  
-   「自動」: このサービスは、コンピューターの起動時に開始を試みます。  
  
-   「無効」: このサービスは開始できません。  
  
 **状態**  
 このサービスが実行中か、停止しているか、無効になっているかが表示されます。 **[...]**の場合は、状態の変更が保留になっています。  
  
  
