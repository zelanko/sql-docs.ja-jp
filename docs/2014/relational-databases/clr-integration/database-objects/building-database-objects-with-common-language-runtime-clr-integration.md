---
title: 共通言語ランタイム (CLR) 統合によるデータベースオブジェクトの構築 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8dc507d455636bf6256fd7ba4649dba53d32884e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919253"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a>CLR (共通言語ランタイム) 統合によるデータベース オブジェクトの構築
  "CLR ルーチン" と呼ばれる[!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を使用してデータベースオブジェクトを構築できます。 CLR ルーチンには、次のものがあります。  
  
-   スカラー UDF (ユーザー定義スカラー値関数)  
  
-   ユーザー定義 TVF (テーブル値関数)  
  
-   UDP (ユーザー定義プロシージャ)  
  
-   ユーザー定義トリガー  
  
 CLR ルーチンは、マネージド コード内ではそれぞれ同じ構造になります。 CLR ルーチンは、クラスの public static ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET では shared) メソッドにマップされます。 ルーチン以外に、.NET Framework を使用して UDT (ユーザー定義型) やユーザー定義集計関数を定義することもできます。 UDT とユーザー定義集計は、.NET Framework クラス全体にマップされます。  
  
 .NET Framework ルーチンの各型には[!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] 、同等[!INCLUDE[tsql](../../../includes/tsql-md.md)]のを使用できるがあります。 たとえば、スカラー UDF は任意のスカラー式で使用できます。 また、TVF は任意の FROM 句で使用できます。 プロシージャは、EXEC ステートメントやクライアント アプリケーションから呼び出すことができます。  
  
> [!NOTE]  
>  効果的であるとクエリ オプティマイザーで判断された場合は、共通言語ランタイムでの CLR オブジェクト (ユーザー定義関数、ユーザー定義型、またはトリガー) の実行を複数のスレッドで行うことができます (並列プラン)。 ただし、ユーザー定義関数がデータにアクセスする場合は、直列プランで実行されます。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] よりも前のサーバー バージョンで実行したときに、ユーザー定義関数に LOB パラメーターが含まれていたり、ユーザー定義関数から値が返される場合も、直列プランで実行する必要があります。  
  
 次の表に、このセクションで説明するトピックの一覧を示します。  
  
 [CLR 統合の概要](getting-started-with-clr-integration.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と CLR との統合を使用したオブジェクトのコンパイルに必要なライブラリと名前空間の概要について説明します。 また、例として "Hello World" CLR ストアド プロシージャを紹介します。  
  
 [サポートされている .NET Framework ライブラリ](supported-net-framework-libraries.md)  
 CLR 統合でサポートされる .NET Framework ライブラリに関する情報を提供します。  
  
 [CLR 統合プログラミング モデルの制限事項](clr-integration-programming-model-restrictions.md)  
 CLR 統合プログラミング モデルの制限事項に関する情報を提供します。  
  
 [.NET Framework での SQL Server データ型](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と、.NET Framework での同等のデータ型の概要について説明します。  
  
 [CLR 統合のカスタム属性の概要](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 CLR 統合のカスタム属性に関する情報を提供します。  
  
 [CLR ユーザー定義関数](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 テーブル値関数、スカラー関数、ユーザー定義集計関数など、さまざまな種類の CLR 関数の実装方法と使用方法について説明します。  
  
 [CLR ユーザー定義型](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 CLR のユーザー定義型を実装して使用する方法について説明します。  
  
 [CLR ストアド プロシージャ](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 CLR のストアド プロシージャを実装して使用する方法について説明します。  
  
 [CLR トリガー](../../../database-engine/dev-guide/clr-triggers.md)  
 CLR のトリガーを実装して使用する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [CLR&#41; 統合の概要 &#40;共通言語ランタイム](../common-language-runtime-integration-overview.md)  
  
  
