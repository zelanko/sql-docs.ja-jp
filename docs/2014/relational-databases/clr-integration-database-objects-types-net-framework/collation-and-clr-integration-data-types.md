---
title: 照合順序と CLR 統合データ型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a5b0367487aeb80355b8c5c976818e1b6c1ac04
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954842"
---
# <a name="collation-and-clr-integration-data-types"></a>照合順序と CLR 統合データ型
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] では、`CompareInfo` オブジェクトで照合順序が処理されます。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の文字列 API (アプリケーション プログラミング インターフェイス) では、文字列比較を実行するために、現在のスレッドの `CompareInfo` オブジェクトに関連付けられた `CultureInfo` プロパティを使用します。 オブジェクトの既定の設定は、が実行されている `CultureInfo` [!INCLUDE[msCoName](../../includes/msconame-md.md)] コンピューターの Windows ロケール設定に基づいてい [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 `CultureInfo` 値の比較の既定の比較セマンティクスは、`System.String` が明示的に指定されていなければ、この設定で決定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`CompareInfo` プロパティをデータベースまたはサーバーの照合順序に明示的に変更できせん。 必要であれば、適切な `CompareInfo` プロパティをユーザーがルーチン内で設定します。  
  
## <a name="parameter-collation"></a>パラメーターの照合順序  
 CLR (共通言語ランタイム) ルーチンを作成するとき、そのルーチンにバインドされた CLR メソッドのパラメーターの型が `SQLString` の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、呼び出し元のルーチンを含むデータベースの既定の照合順序でパラメーターのインスタンスが作成されます。 パラメーターが `SqlType` ではない場合 (たとえば、`String` ではなく `SQLString` の場合)、データベースからの照合順序情報はパラメーターに関連付けられません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](sql-server-data-types-in-the-net-framework.md)  
  
  
