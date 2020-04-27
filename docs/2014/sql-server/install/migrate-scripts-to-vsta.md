---
title: スクリプトを VSTA | に移行するMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cb44a7b635e24c0c2e3266c1cca98a9c4f6a347c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093986"
---
# <a name="migrate-scripts-to-vsta"></a>VSTA へのスクリプトの移行
  パッケージをに[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]アップグレードすると[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 、では、スクリプトタスクまたはスクリプトコンポーネント内[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]のスクリプトが Tools for Applications (VSTA) に移行されます。 VSTA は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で使用されるスクリプト環境です。 で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]は、の[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スクリプト環境は[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA) です。  
  
 スクリプト タスクまたはスクリプト コンポーネント内のスクリプトでインターフェイスを参照している場合、パッケージをアップグレードする前にそれらの参照の変更が必要になる場合があります。 参照を変更しないと、使用するアップグレード方法によってはパッケージをアップグレードできないかスクリプトを検証できません。 これらの参照を変更するには、IDTS*xxx*90 インターフェイスへの参照を、対応する idts*xxx*100 インターフェイスへの参照に置き換えます。  
  
 スクリプトの移行方法とパッケージのアップグレード方法の詳細については、「 [Integration Services パッケージのアップグレード](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
## <a name="understanding-migration-failures"></a>移行エラーについて  
 スクリプトを移行する際、次の理由により移行が失敗することがあります。  
  
-   VSA スクリプトのエントリ ポイント名が変更された。  
  
     エントリ ポイントは、スクリプト タスク コードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムが呼び出す、VSTA プロジェクトの `ScriptMain` クラスのメソッドを指定します。 `ScriptMain`クラスは、スクリプトテンプレートによって生成される既定のクラスです。  
  
-   VSA スクリプトにエントリ ポイントがないか、複数のエントリ ポイントがある。  
  
-   アセンブリ参照を追加できなかった。  
  
-   `ScriptMain` クラスが、`ScriptObjectModelSSIS` クラス以外にもクラスを継承するように変更された。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]では、多重継承はサポートされていません。  
  
 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)]を使用する VSA スクリプトを、を使用[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]する VSTA スクリプトに変換することはできません。 ただし、を使用[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]する新しい VSTA スクリプトを作成できます。 詳細については、「[スクリプト タスクのコーディングおよびデバッグ](../../integration-services/control-flow/script-task.md)」および「[スクリプト コンポーネントのコーディングおよびデバッグ](../../integration-services/data-flow/transformations/script-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スクリプトによるパッケージの拡張](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
