---
title: 照合順序と CLR 統合データ型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 56206f6273b413a66a72b2a2c72ed3593b2f9a66
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354684"
---
# <a name="collation-and-clr-integration-data-types"></a>照合順序と CLR 統合データ型
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] では、`CompareInfo` オブジェクトで照合順序が処理されます。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の文字列 API (アプリケーション プログラミング インターフェイス) では、文字列比較を実行するために、現在のスレッドの `CompareInfo` オブジェクトに関連付けられた `CultureInfo` プロパティを使用します。 既定の設定、`CultureInfo`オブジェクトがに基づいて、[!INCLUDE[msCoName](../../includes/msconame-md.md)]となるコンピューターの Windows ロケール設定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 `CultureInfo` 値の比較の既定の比較セマンティクスは、`System.String` が明示的に指定されていなければ、この設定で決定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`CompareInfo` プロパティをデータベースまたはサーバーの照合順序に明示的に変更できせん。 必要であれば、適切な `CompareInfo` プロパティをユーザーがルーチン内で設定します。  
  
## <a name="parameter-collation"></a>パラメーターの照合順序  
 CLR (共通言語ランタイム) ルーチンを作成するとき、そのルーチンにバインドされた CLR メソッドのパラメーターの型が `SQLString` の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、呼び出し元のルーチンを含むデータベースの既定の照合順序でパラメーターのインスタンスが作成されます。 パラメーターが `SqlType` ではない場合 (たとえば、`String` ではなく `SQLString` の場合)、データベースからの照合順序情報はパラメーターに関連付けられません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](sql-server-data-types-in-the-net-framework.md)  
  
  
