---
title: 照合順序と CLR 統合データ型 |Microsoft Docs
description: SQL Server CLR 統合では、.NET Framework 文字列 Api は、現在のスレッドの CultureInfo の CompareInfo プロパティを使用して、文字列比較を実行します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: 46e4d450db90e4bfc93187a48ca8adae472036c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488496"
---
# <a name="collation-and-clr-integration-data-types"></a>照合順序と CLR 統合データ型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]では、 **compareinfo**オブジェクトが照合順序を処理します。 文字列[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]アプリケーションプログラミングインターフェイス (api) は、現在のスレッドの**CultureInfo**オブジェクトに関連付けられている**compareinfo**プロパティを使用して、文字列比較を実行します。 **CultureInfo**オブジェクトの既定の設定は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されているコンピューターの Windows ロケール設定に基づいています。 これにより、 **system.string**値の比較のために、明示的な**CultureInfo**が指定されていない場合の既定の比較セマンティクスが決まります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、 **Compareinfo**プロパティをデータベースまたはサーバーの照合順序に明示的に変更しません。 必要に応じて、ユーザーはルーチンで適切な**Compareinfo**プロパティを設定する必要があります。  
  
## <a name="parameter-collation"></a>パラメーターの照合順序  
 共通言語ランタイム (clr) ルーチンを作成し、そのルーチンにバインドされた clr メソッドのパラメーターが**SQLString**型である場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、は、呼び出し元のルーチンを含むデータベースの既定の照合順序を使用して、パラメーターのインスタンスを作成します。 パラメーターが**SqlType**ではない場合 (たとえば、 **SQLString**ではなく**文字列**の場合)、データベースからの照合順序情報はパラメーターに関連付けられません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
