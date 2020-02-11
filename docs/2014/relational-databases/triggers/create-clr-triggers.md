---
title: CLR トリガーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b68531b962b10785927c6212b2483f2d9c1d7d3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62698829"
---
# <a name="create-clr-triggers"></a>CLR トリガーの作成
  内[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]共通言語ランタイム (CLR) で作成されたアセンブリでプログラミングされているデータベースオブジェクトを作成できます。 CLR で提供される豊富なプログラミング モデルを利用できるデータベース オブジェクトには、DML トリガー、DDL トリガー、ストアド プロシージャ、関数、集計関数、型などがあります。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の CLR トリガー (DML トリガーまたは DDL トリガー) を作成するには、次の手順を実行します。  
  
-   トリガーを .NET Framework でサポートされる言語でクラスとして定義します。 CLR でのトリガーのプログラミング方法の詳細については、「 [CLR トリガー](../../database-engine/dev-guide/clr-triggers.md)」をご覧ください。 次に、適切な言語コンパイラを使用してクラスをコンパイルし、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] のアセンブリをビルドします。  
  
-   CREATE ASSEMBLY ステートメントを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアセンブリを登録します。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアセンブリを使用した作業方法の詳細については、「[アセンブリ &#40;データベース エンジン&#41;](../clr-integration/assemblies-database-engine.md)」をご覧ください。  
  
-   登録したアセンブリを参照するトリガーを作成します。  
  
> [!NOTE]  
>  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] で SQL Server プロジェクトを配置すると、そのプロジェクトで指定されたデータベースにアセンブリが登録されます。 また、プロジェクトを配置することで、`SqlTrigger` 属性で注釈が付けられたすべてのメソッドの CLR トリガーがデータベースに作成されます。 詳細については、「 [CLR データベース オブジェクトの配置](../clr-integration/deploying-clr-database-objects.md)」を参照してください。  
  
> [!NOTE]  
>  CLR コードを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能は、既定では無効になっています。 マネージコードモジュールを参照するデータベースオブジェクトを作成、変更、および削除することはできますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [sp_configure (transact-sql)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)を使用して[clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)を有効にしない限り、これらの参照はでは実行されません。  
  
 **アセンブリを作成、変更、または削除するには**  
  
-   [CREATE ASSEMBLY &#40;Transact-sql&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **CLR トリガーを作成するには**  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a>参照  
 [DML トリガー](dml-triggers.md)   
 [共通言語ランタイム &#40;CLR&#41; 統合プログラミングの概念](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [CLR データベース オブジェクトからのデータ アクセス](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
