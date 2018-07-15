---
title: 照合順序と CLR 統合データ型 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
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
ms.openlocfilehash: 31bb87caa5d5b997c3e99478fc3308fc03d4f956
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357704"
---
# <a name="collation-and-clr-integration-data-types"></a>照合順序と CLR 統合データ型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]、 **CompareInfo**オブジェクトは照合順序を処理します。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]アプリケーション プログラミング インターフェイス (Api) を使用して、文字列、 **CompareInfo**プロパティに関連付けられている、 **CultureInfo**文字列比較を実行する現在のスレッドのオブジェクト。 既定の設定、 **CultureInfo**オブジェクトがに基づいて、[!INCLUDE[msCoName](../../includes/msconame-md.md)]となるコンピューターの Windows ロケール設定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 明示的な場合、既定の比較セマンティクスを決定します**CultureInfo**比較の指定された**System.String**値。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 明示的に変更していない、 **CompareInfo**データベースまたはサーバーの照合順序のプロパティ。 必要な場合、適切なユーザーを設定する必要があります**CompareInfo**がルーチン内でのプロパティ。  
  
## <a name="parameter-collation"></a>パラメーターの照合順序  
 型のルーチンは、共通言語ランタイム (CLR) のルーチンを作成すると、CLR メソッドのパラメーターのバインドを**SQLString**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースの既定の照合順序でパラメーターのインスタンスを作成します。呼び出し元のルーチンを含むです。 パラメーターがない場合、 **SqlType** (たとえば、**文字列**なく**SQLString**)、データベースの照合順序情報は、パラメーターに関連付けられていません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
