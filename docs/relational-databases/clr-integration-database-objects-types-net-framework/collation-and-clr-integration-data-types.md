---
title: 照合順序と CLR 統合データ型 |マイクロソフトドキュメント
description: SQL Server CLR 統合では、.NET フレームワーク文字列 API は、現在のスレッドの CultureInfo の CompareInfo プロパティを使用して文字列比較を実行します。
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488496"
---
# <a name="collation-and-clr-integration-data-types"></a>照合順序と CLR 統合データ型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]では、 **CompareInfo**オブジェクトが照合順序を処理します。 文字列アプリケーション プログラミング インターフェイス (API) は、現在のスレッドの**CultureInfo**オブジェクトに関連付けられた**CompareInfo**プロパティを使用して、文字列比較を実行します。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **CultureInfo**オブジェクトの既定の設定は、実行している[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューターの Windows ロケール設定に基づいています。 これは、明示的な**CultureInfo**が指定されていない場合に **、System.String**値の比較に使用する既定の比較セマンティクスを決定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、データベースまたはサーバー照合順序に**対して、CompareInfo**プロパティを明示的に変更しません。 必要に応じて、ユーザーはルーチンで適切な**CompareInfo**プロパティを設定する必要があります。  
  
## <a name="parameter-collation"></a>パラメーターの照合順序  
 共通言語ランタイム (CLR) ルーチンを作成し、CLR メソッドのパラメーターが**SQLString**型である場合、呼び出[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しルーチンを含むデータベースの既定の照合順序を持つパラメーターのインスタンスが作成されます。 パラメーターが**SqlType**ではない場合 (たとえば **、SQLString**ではなく**文字列**) は、データベースからの照合順序情報はパラメーターに関連付けされません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
