---
title: "CLR ルーチンのカスタム属性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
caps.latest.revision: "82"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d1ddfeafa4d4b678a9fb20bb597e9fd041bb201
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>CLR ルーチンの場合、CLR 統合のカスタム属性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]共通言語ランタイム (CLR) のルーチン、ユーザー定義型、およびユーザー定義集計に登録されているを一覧表示される属性を適用できます[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 属性が適用されない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は既定値を想定します。 表示されている属性が定義されている、 **Microsoft.SqlServer.Server**名前空間。  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>SqlUserDefinedAggregate 属性  
 **SqlUserDefinedAggregate**属性は、ユーザー定義集計として登録する必要がありますメソッドを示します。 すべてのユーザー定義集計にこのカスタム属性で注釈を付ける必要があります。  
  
 詳細については、次を参照してください。 [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626)です。  
  
## <a name="the-sqlfunction-attribute"></a>SqlFunction 属性  
 **SqlFunction**属性は、適切な関数属性セットを持つ、関数として登録する必要があります、メソッドを示します。  
  
 詳細については、次を参照してください。 [SqlFunctionAttribute](http://go.microsoft.com/fwlink/?LinkId=128019)です。  
  
## <a name="the-sqlfacet-attribute"></a>SqlFacet 属性  
 **SqlFacet**属性は、ユーザー定義型 (UDT) の式の戻り値の型に関する情報を返すために使用します。  
  
 詳細については、次を参照してください。 [SqlFacetAttribute](http://go.microsoft.com/fwlink/?LinkId=128020)です。  
  
## <a name="the-sqlprocedure-attribute"></a>SqlProcedure 属性  
 **SqlProcedure**属性は、メソッドは、ストアド プロシージャとして登録するかを示します。 この属性は、Visual Studio だけで使用され、指定されたメソッドがストアド プロシージャとして自動的に登録されます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では使用されません。  
  
 詳細については、次を参照してください。 [SqlProcedureAttribute](http://go.microsoft.com/fwlink/?LinkId=128021)です。  
  
## <a name="the-sqltrigger-attribute"></a>SqlTrigger 属性  
 **SqlTrigger**属性は、メソッドは、トリガーとして登録するかを示します。  
  
 詳細については、次を参照してください。 [SqlTriggerContext](http://go.microsoft.com/fwlink/?LinkId=128022)と[SqlTriggerAttribute](http://go.microsoft.com/fwlink/?LinkId=203898)です。  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 SqlUserDefinedTypeAttribute をアセンブリのクラス定義に適用できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、これにより、このカスタム属性を持つクラス定義にバインドされたユーザー定義型が作成されます。  
  
 詳細については、次を参照してください。 [SqlUserDefinedTypeAttribute](http://go.microsoft.com/fwlink/?LinkId=128024)です。  
  
## <a name="the-sqlmethod-attribute"></a>SqlMethod 属性  
 **SqlMethod**の UDT 上でプロパティまたはメソッドの決定性とデータ アクセス プロパティを示すために属性を使用します。  
  
 詳細については、次を参照してください。 [SqlMethodAttribute](http://go.microsoft.com/fwlink/?LinkId=128025)です。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義集計](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [CLR ユーザー定義関数](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR ユーザー定義型](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ストアド プロシージャ](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [CLR トリガー](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
