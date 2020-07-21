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
ms.openlocfilehash: 041b46383232f3784c1c817f8feb726f382e1ec5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054721"
---
# <a name="migrate-scripts-to-vsta"></a>VSTA へのスクリプトの移行
  パッケージをにアップグレードすると [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] スクリプトタスクまたはスクリプトコンポーネント内のスクリプトが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) に移行されます。 VSTA は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で使用されるスクリプト環境です。 で [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] は、のスクリプト環境 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA) です。  
  
 スクリプト タスクまたはスクリプト コンポーネント内のスクリプトでインターフェイスを参照している場合、パッケージをアップグレードする前にそれらの参照の変更が必要になる場合があります。 参照を変更しないと、使用するアップグレード方法によってはパッケージをアップグレードできないかスクリプトを検証できません。 これらの参照を変更するには、IDTS*xxx*90 インターフェイスへの参照を、対応する idts*xxx*100 インターフェイスへの参照に置き換えます。  
  
 スクリプトの移行方法とパッケージのアップグレード方法の詳細については、「 [Integration Services パッケージのアップグレード](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
## <a name="understanding-migration-failures"></a>移行エラーについて  
 スクリプトを移行する際、次の理由により移行が失敗することがあります。  
  
-   VSA スクリプトのエントリ ポイント名が変更された。  
  
     エントリ ポイントは、スクリプト タスク コードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムが呼び出す、VSTA プロジェクトの `ScriptMain` クラスのメソッドを指定します。 クラスは、スクリプトテンプレートによって `ScriptMain` 生成される既定のクラスです。  
  
-   VSA スクリプトにエントリ ポイントがないか、複数のエントリ ポイントがある。  
  
-   アセンブリ参照を追加できなかった。  
  
-   `ScriptMain` クラスが、`ScriptObjectModelSSIS` クラス以外にもクラスを継承するように変更された。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]では、多重継承はサポートされていません。  
  
 を使用する VSA スクリプトを、 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] を使用する VSTA スクリプトに変換することはできません [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] 。 ただし、を使用する新しい VSTA スクリプトを作成でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] ます。 詳細については、「[スクリプト タスクのコーディングおよびデバッグ](../../integration-services/control-flow/script-task.md)」および「[スクリプト コンポーネントのコーディングおよびデバッグ](../../integration-services/data-flow/transformations/script-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スクリプトによるパッケージの拡張](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
