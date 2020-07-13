---
title: CLR ユーザー定義関数 |Microsoft Docs
description: SQL Server CLR 統合を使用すると、ユーザー定義のスカラー値関数、テーブル値関数、および集計関数を任意の .NET Framework プログラミング言語で作成できます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: fe481b1a49f8eba69bbf913e49f398c86244b952
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727861"
---
# <a name="clr-user-defined-functions"></a>CLR ユーザー定義関数
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  ユーザー定義関数は、パラメーターを受け取り、計算やその他の動作を実行し、結果を返すルーチンです。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] からは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# などの [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework プログラミング言語でユーザー定義関数を記述できます。  
  
 関数には、1 つの値を返すスカラー関数と行セットを返すテーブル値関数の 2 種類があります。  
  
 次の表に、このセクションの各トピックの一覧を示します。  
  
 [CLR スカラー値関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-scalar-valued-functions.md)  
 実装の要件とスカラー値関数の例について説明します。  
  
 [CLR テーブル値関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
 TVF (テーブル値関数) の実装方法と使用方法を説明し、[!INCLUDE[tsql](../../includes/tsql-md.md)] TVF と CLR (共通言語ランタイム) TVF の相異点についても説明します。  
  
 [CLR ユーザー定義集計](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)  
 ユーザー定義集計の実装方法と使用方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [ユーザー定義関数](../../relational-databases/user-defined-functions/user-defined-functions.md)  
  
  
