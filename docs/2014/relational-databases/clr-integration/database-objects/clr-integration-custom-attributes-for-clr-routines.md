---
title: CLR ルーチンのカスタム属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
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
caps.latest.revision: 82
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a2f3e1980c164327e584d8f485c2d08571534245
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351044"
---
# <a name="custom-attributes-for-clr-routines"></a>CLR ルーチンのカスタム属性
  共通言語ランタイム (CLR) のルーチン、ユーザー定義型、および登録されているユーザー定義集計に示されている属性を適用できる[!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]します。 属性が適用されない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は既定値を想定します。 ここで示す属性は、`Microsoft.SqlServer.Server` 名前空間で定義されています。  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>SqlUserDefinedAggregate 属性  
 `SqlUserDefinedAggregate` 属性は、ユーザー定義集計として登録する必要のあるメソッドを示します。 すべてのユーザー定義集計にこのカスタム属性で注釈を付ける必要があります。  
  
 詳細については、次を参照してください。 [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626)します。  
  
## <a name="the-sqlfunction-attribute"></a>SqlFunction 属性  
 `SqlFunction` 属性は、関数として登録する必要のあるメソッドを示します。この属性を使用する場合は、適切な関数属性セットを指定します。  
  
 詳細については、次を参照してください。 [SqlFunctionAttribute](http://go.microsoft.com/fwlink/?LinkId=128019)します。  
  
## <a name="the-sqlfacet-attribute"></a>SqlFacet 属性  
 `SqlFacet` 属性は、UDT (ユーザー定義型) 式の戻り値の型についての情報を返すために使用します。  
  
 詳細については、次を参照してください。 [SqlFacetAttribute](http://go.microsoft.com/fwlink/?LinkId=128020)します。  
  
## <a name="the-sqlprocedure-attribute"></a>SqlProcedure 属性  
 `SqlProcedure` 属性は、ストアド プロシージャとして登録する必要のあるメソッドを示します。 この属性は、Visual Studio だけで使用され、指定されたメソッドがストアド プロシージャとして自動的に登録されます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では使用されません。  
  
 詳細については、次を参照してください。 [SqlProcedureAttribute](http://go.microsoft.com/fwlink/?LinkId=128021)します。  
  
## <a name="the-sqltrigger-attribute"></a>SqlTrigger 属性  
 `SqlTrigger` 属性は、トリガーとして登録する必要のあるメソッドを示します。  
  
 詳細については、次を参照してください。 [SqlTriggerContext](http://go.microsoft.com/fwlink/?LinkId=128022)と[SqlTriggerAttribute](http://go.microsoft.com/fwlink/?LinkId=203898)します。  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 SqlUserDefinedTypeAttribute をアセンブリのクラス定義に適用できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、これにより、このカスタム属性を持つクラス定義にバインドされたユーザー定義型が作成されます。  
  
 詳細については、次を参照してください。 [SqlUserDefinedTypeAttribute](http://go.microsoft.com/fwlink/?LinkId=128024)します。  
  
## <a name="the-sqlmethod-attribute"></a>SqlMethod 属性  
 `SqlMethod` 属性は、UDT のメソッドまたはプロパティの決定性およびデータ アクセス プロパティを示すために使用します。  
  
 詳細については、次を参照してください。 [SqlMethodAttribute](http://go.microsoft.com/fwlink/?LinkId=128025)します。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義集計](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [CLR ユーザー定義関数](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR ユーザー定義型](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ストアド プロシージャ](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [CLR トリガー](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
