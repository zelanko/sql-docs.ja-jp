---
title: VSTA にスクリプトの移行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
caps.latest.revision: 44
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 99acbad66d2a614431bc1f08ad88bd12f2a3e6b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178142"
---
# <a name="migrate-scripts-to-vsta"></a>VSTA にスクリプトを移行します。
  アップグレードするときに[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]パッケージを[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スクリプト タスクまたはスクリプト コンポーネント内のスクリプトが移行[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)。 VSTA は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で使用されるスクリプト環境です。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、ためのスクリプト環境[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]は[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA) です。  
  
 スクリプト タスクまたはスクリプト コンポーネント内のスクリプトでインターフェイスを参照している場合、パッケージをアップグレードする前にそれらの参照の変更が必要になる場合があります。 参照を変更しないと、使用するアップグレード方法によってはパッケージをアップグレードできないかスクリプトを検証できません。 これらの参照を変更するには、IDTS への参照を置き換える*xxx*、対応する IDTS への参照を持つ 90 インターフェイス*xxx*100 インターフェイスです。  
  
 スクリプトの移行およびパッケージをアップグレードする方法の詳細については、次を参照してください。 [Integration Services パッケージのアップグレード](../../integration-services/install-windows/upgrade-integration-services-packages.md)です。  
  
## <a name="understanding-migration-failures"></a>移行エラーについて  
 スクリプトを移行する際、次の理由により移行が失敗することがあります。  
  
-   VSA スクリプトのエントリ ポイント名が変更された。  
  
     エントリ ポイントは、スクリプト タスク コードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムが呼び出す、VSTA プロジェクトの `ScriptMain` クラスのメソッドを指定します。 `ScriptMain`クラスは、スクリプト テンプレートを生成する既定のクラスです。  
  
-   VSA スクリプトにエントリ ポイントがないか、複数のエントリ ポイントがある。  
  
-   アセンブリ参照を追加できなかった。  
  
-   `ScriptMain` クラスが、`ScriptObjectModelSSIS` クラス以外にもクラスを継承するように変更された。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 複数の継承をサポートしません。  
  
 使用する VSA スクリプトを変換することはできません[!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)]を使用する VSTA スクリプトに[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]です。 ただし、使用する新しい VSTA スクリプトを作成できます[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]です。 詳細については、「[スクリプト タスクのコーディングおよびデバッグ](../../integration-services/control-flow/script-task.md)」および「[スクリプト コンポーネントのコーディングおよびデバッグ](../../integration-services/data-flow/transformations/script-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スクリプトによるパッケージの拡張](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  