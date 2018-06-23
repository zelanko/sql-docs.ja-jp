---
title: 複数の優先順位制約 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d4a9dc0f4b40320533828e2b1ef9f5f4cdfab9c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084351"
---
# <a name="multiple-precedence-constraints"></a>複数の優先順位制約
  優先順位制約は、2 つのタスク、2 つのコンテナー、1 つのタスクと 1 つのコンテナーなど、2 つの実行可能ファイルを連結します。 これらは優先順位付き実行可能ファイル、および制約付き実行可能ファイルと呼ばれています。 制約付き実行可能ファイルには、複数の優先順位制約を含めることができます。 優先順位制約の詳細については、「[優先順位制約](control-flow/precedence-constraints.md)」を参照してください。  
  
 制約をグループ化して複雑な制約シナリオを組み立てると、複雑な制御フローをパッケージに実装できます。 たとえば、次の図でタスク D はリンクによってタスク A に、`Success`によってタスク B にリンクされている制約は、タスク D、`Failure`によってタスク C にリンクされている制約、およびタスク D、`Success`制約。 タスク D とタスク A の間、タスク D とタスク B の間、およびタスク D とタスク C の間の優先順位制約は、論理 *AND* リレーションシップになります。 したがって、タスク D を実行するには、タスク A の実行が成功し、タスク B が失敗し、タスク C の実行が成功する必要があります。  
  
 ![優先順位制約によってリンクされているタスク](media/precedenceconstraints.gif "優先順位制約によってリンクされているタスク")  
  
## <a name="logicaland-property"></a>LogicalAnd プロパティ  
 タスクまたはコンテナーに複数の制約がある場合、`LogicalAnd` プロパティにより、優先順位制約を単独で評価するか、別の制約と組み合わせて評価するかを指定します。  
  
 設定することができます、`LogicalAnd`プロパティを使用して、**優先順位制約エディター**で[!INCLUDE[ssIS](../includes/ssis-md.md)]デザイナー、または [プロパティ] ウィンドウを[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を提供します。  
  
## <a name="related-tasks"></a>Related Tasks  
 [優先順位制約のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  