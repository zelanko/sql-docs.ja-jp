---
title: 複数の優先順位制約 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 61939b09b4a4365c09089df2b52026e96f9427ee
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965152"
---
# <a name="multiple-precedence-constraints"></a>複数の優先順位制約
  優先順位制約は、2 つのタスク、2 つのコンテナー、1 つのタスクと 1 つのコンテナーなど、2 つの実行可能ファイルを連結します。 これらは優先順位付き実行可能ファイル、および制約付き実行可能ファイルと呼ばれています。 制約付き実行可能ファイルには、複数の優先順位制約を含めることができます。 詳細については、「 [優先順位制約](control-flow/precedence-constraints.md)」を参照してください。  
  
 制約をグループ化して複雑な制約シナリオを組み立てると、複雑な制御フローをパッケージに実装できます。 たとえば、次の図で、タスク D は、`Success` 制約によってタスク A にリンクされ、`Failure` 制約によってタスク B にリンクされ、さらに `Success` 制約によってタスク C にリンクされています。 タスク D とタスク A の間、タスク D とタスク B の間、およびタスク D とタスク C の間の優先順位制約は、論理 *AND* リレーションシップになります。 したがって、タスク D を実行するには、タスク A の実行が成功し、タスク B が失敗し、タスク C の実行が成功する必要があります。  
  
 ![優先順位制約によってリンクされたタスク](media/precedenceconstraints.gif "優先順位制約によってリンクされたタスク")  
  
## <a name="logicaland-property"></a>LogicalAnd プロパティ  
 タスクまたはコンテナーに複数の制約がある場合、`LogicalAnd` プロパティにより、優先順位制約を単独で評価するか、別の制約と組み合わせて評価するかを指定します。  
  
 プロパティを設定するには、 `LogicalAnd` デザイナーの [**優先順位制約エディター** ] を使用するか、に用意されているプロパティウィンドウを使用し [!INCLUDE[ssIS](../includes/ssis-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。  
  
## <a name="related-tasks"></a>Related Tasks  
 [優先順位制約のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
