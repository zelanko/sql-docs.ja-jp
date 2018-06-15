---
title: 照合順序と CLR 統合データ タイプ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
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
ms.openlocfilehash: ff9f8b52d2b6b9856562a99db288a461a71e0f6b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918837"
---
# <a name="collation-and-clr-integration-data-types"></a>照合順序と CLR 統合データ型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]、 **CompareInfo**オブジェクトは照合順序を処理します。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]文字列のアプリケーション プログラミング インターフェイス (Api) を使用して、 **CompareInfo**プロパティに関連付けられている、 **CultureInfo**現在のスレッドの文字列比較を実行するオブジェクト。 既定の設定、 **CultureInfo**オブジェクトがに基づいて、[!INCLUDE[msCoName](../../includes/msconame-md.md)]いるコンピューターの Windows ロケール設定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 これは、設定で決定既定の比較セマンティクスは、明示的な**CultureInfo**指定すると、比較の**System.String**値。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 明示的に変わらないので、 **CompareInfo**プロパティをデータベースまたはサーバーの照合順序。 必要な場合、ユーザーは、適切な設定する必要があります**CompareInfo**がルーチン内でのプロパティです。  
  
## <a name="parameter-collation"></a>パラメーターの照合順序  
 型のルーチンは、共通言語ランタイム (CLR) のルーチンを作成すると、CLR のメソッドのパラメーターにバインド**SQLString**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースの既定の照合順序でパラメーターのインスタンスを作成呼び出し元のルーチンを含むです。 パラメーターではない場合、 **SqlType** (たとえば、**文字列**なく**SQLString**)、データベースの照合順序情報は、パラメーターに関連付けられていません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
