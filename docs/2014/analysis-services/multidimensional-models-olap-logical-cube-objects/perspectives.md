---
title: パースペクティブ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e77942ff650cc428e957bacc92921cb2b669a04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175841"
---
# <a name="perspectives"></a>パースペクティブ
  パースペクティブは、ユーザーがキューブをより単純な方法で表示するための定義です。 パースペクティブは、キューブの機能のサブセットです。 パースペクティブを使用すると、管理者がキューブのビューを作成できるので、ユーザーは各自にとって重要なデータに集中できます。 パースペクティブには、キューブのすべてのオブジェクトのサブセットが含まれます。 パースペクティブには、親キューブに定義されていない要素を含めることはできません。  
  
 単純な <xref:Microsoft.AnalysisServices.Perspective> オブジェクトは、基本情報、ディメンション、メジャー グループ、計算、KPI、アクションで構成されます。 基本情報には、パースペクティブの名前および既定のメジャーが含まれます。 ディメンションは、キューブ ディメンションのサブセットです。 メジャー グループは、キューブのメジャー グループのサブセットです。 計算は、キューブの計算のサブセットです。 KPI は、キューブの KPI のサブセットです。 アクションは、キューブのアクションのサブセットです。  
  
 キューブを更新して処理するまで、パースペクティブは使用できません。  
  
 キューブはユーザーの探索するための非常に複雑なオブジェクトの場合[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 1 つのキューブで完全なデータ ウェアハウスのコンテンツを表現することができ、キューブ内の複数のメジャー グループで複数のファクト テーブルを表したり、複数のディメンション テーブルに基づいた複数のディメンションを伴うことがあります。 このようなキューブは非常に複雑で強力ですが、ビジネス インテリジェンス要件やレポート要件を満たすために、キューブのごく一部分しか操作する必要のないユーザーにとっては大きな負担になります。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、パースペクティブを使用するには、キューブ内の見かけ上の複雑さを軽減する[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 パースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをキューブに対して的を絞って作成するための、表示可能なサブセットを定義できます。 パースペクティブにより、キューブに含まれるオブジェクトの表示設定が決定されます。 パースペクティブでは、次のオブジェクトの表示または非表示が可能です。  
  
-   ディメンション  
  
-   属性  
  
-   階層  
  
-   メジャー グループ  
  
-   メジャー  
  
-   主要業績評価指標 (Kpi)  
  
-   計算 (計算されるメンバー、名前付きセット、スクリプト コマンド)  
  
-   アクション  
  
 たとえば、 **Adventure Works**でキューブ、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースには、11 個のメジャー グループおよび売上、売上予測を表す、21 の別のキューブ ディメンションと財務のデータが含まれています。 クライアント アプリケーションは完全なキューブを直接参照できますが、基本的な売上予測情報を抽出しようとしているユーザーにとって、このビューポイントでは扱いづらい可能性があります。 代わりに、同じユーザーが使用できる、**売上目標**の表示を制限するためのパースペクティブ、 **Adventure Works**キューブ売上予測に関連するオブジェクトのみにします。  
  
 パースペクティブでユーザーに表示されないキューブ内のオブジェクトでも、XML for Analysis (XMLA)、多次元式 (MDX)、またはデータ マイニング式 (DMX) のステートメントを使用して、直接参照し取得することができます。 パースペクティブはキューブ内のオブジェクトへのアクセスを制限するものではありません。そのような目的で使用しないでください。パースペクティブは、キューブへのアクセスをより快適にするために使用するものです。  
  
 パースペクティブはキューブの読み取り専用ビューであり、パースペクティブを使用してキューブ内のオブジェクトを変更したり、名前を変更したりすることはできません。 同様に、パースペクティブを使用して表示部分の合計などのキューブの動作や機能を変更することもできません。  
  
## <a name="security"></a>Security  
 パースペクティブは、セキュリティ メカニズムとして使用するためのものではなく、ビジネス インテリジェンス アプリケーションでのユーザーの使用体験をより良いものにするためのツールとして使用するものです。 特定のパースペクティブのセキュリティはすべて、基になるキューブから継承されます。 たとえば、パースペクティブでは、ユーザーがアクセス権を持っていないキューブ内のオブジェクトにアクセスできません。 パースペクティブでキューブのオブジェクトへのアクセスが提供されるようにするには、そのキューブのセキュリティを解決しておく必要があります。  
  
  