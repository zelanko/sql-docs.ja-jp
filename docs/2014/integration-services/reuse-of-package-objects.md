---
title: パッケージ オブジェクトの再利用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b7612cb2684bb842108068b062e54fbe9dee4327
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422929"
---
# <a name="reuse-of-package-objects"></a>パッケージ オブジェクトの再利用
  多くの場合、パッケージには、再利用できるような機能が含まれています。 たとえば、一連のタスクを作成した場合、それらのアイテムを合わせてグループとして再利用したり、別の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトで作成した接続マネージャーのように、1 つのアイテムを再利用したりすることができます。  
  
## <a name="copy-and-paste"></a>コピーと貼り付け  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] と [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでは、制御フロー アイテム、データ フロー アイテム、接続マネージャーなど、パッケージ オブジェクトのコピーと貼り付けがサポートされます。 コピーと貼り付けは、プロジェクト間およびパッケージ間で行うことができます。 複数のプロジェクトがソリューションに含まれている場合、プロジェクト間でコピーを実行でき、それらのプロジェクトの種類は異なってもかまいません。  
  
 1 つのソリューションに複数のパッケージが含まれている場合、それらのパッケージ間でコピーと貼り付けを行うことができます。 パッケージは、同じ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトに含まれていても、異なる Integration Services プロジェクトに含まれていてもかまいません。 ただし、パッケージ オブジェクトは他のオブジェクトに依存し、その依存関係がなければ成立しない場合があります。 たとえば、SQL 実行タスクは接続マネージャーを使用します。タスクを正しく機能させるには、この接続マネージャーもコピーする必要があります。 また、パッケージ オブジェクトによっては、特定のオブジェクトが既にパッケージに含まれている必要があるものもあります。このオブジェクトがなければ、コピーしたオブジェクトをパッケージに正常に貼り付けることができません。 たとえば、1 つもデータ フロー タスクを含まないパッケージには、データ フローを貼り付けることはできません。  
  
 同じパッケージを何度もコピーして使用する場合もあります。 このようなコピー プロセスを回避するには、そのパッケージをテンプレートとして指定すれば、新しいパッケージを作成するときに使用できます。  
  
 パッケージ オブジェクトをコピーすると、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] により、新しい GUID が新しいオブジェクトの `ID` プロパティに自動的に割り当てられ、`Name` プロパティが自動的に更新されます。  
  
 変数はコピーできません。 タスクなどのオブジェクトで変数が使用される場合は、コピー先のパッケージにその変数を再作成する必要があります。 これに対して、パッケージ全体をコピーした場合は、パッケージの変数もコピーされます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [パッケージ オブジェクトをコピーする](../../2014/integration-services/copy-package-objects.md)  
  
-   [プロジェクト アイテムをコピーする](../../2014/integration-services/copy-project-items.md)  
  
-   [パッケージをパッケージ テンプレートとして保存する](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
