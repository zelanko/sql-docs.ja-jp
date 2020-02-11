---
title: CLR ルーチンのカスタム属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 817591cec64a4210c4cc573588be1b8ac6dfb8a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62873809"
---
# <a name="custom-attributes-for-clr-routines"></a>CLR ルーチンのカスタム属性
  ここに示されている属性は、に[!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]登録されている共通言語ランタイム (CLR) ルーチン、ユーザー定義型、およびユーザー定義集計に適用できます。 属性が適用されない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は既定値を想定します。 ここで示す属性は、`Microsoft.SqlServer.Server` 名前空間で定義されています。  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>SqlUserDefinedAggregate 属性  
 
  `SqlUserDefinedAggregate` 属性は、ユーザー定義集計として登録する必要のあるメソッドを示します。 すべてのユーザー定義集計にこのカスタム属性で注釈を付ける必要があります。  
  
 詳細については、「 [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)」を参照してください。  
  
## <a name="the-sqlfunction-attribute"></a>SqlFunction 属性  
 
  `SqlFunction` 属性は、関数として登録する必要のあるメソッドを示します。この属性を使用する場合は、適切な関数属性セットを指定します。  
  
 詳細については、「 [Sqlfunctionattribute](https://go.microsoft.com/fwlink/?LinkId=128019)」を参照してください。  
  
## <a name="the-sqlfacet-attribute"></a>SqlFacet 属性  
 
  `SqlFacet` 属性は、UDT (ユーザー定義型) 式の戻り値の型についての情報を返すために使用します。  
  
 詳細については、「 [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)」を参照してください。  
  
## <a name="the-sqlprocedure-attribute"></a>SqlProcedure 属性  
 
  `SqlProcedure` 属性は、ストアド プロシージャとして登録する必要のあるメソッドを示します。 この属性は、Visual Studio だけで使用され、指定されたメソッドがストアド プロシージャとして自動的に登録されます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では使用されません。  
  
 詳細については、「 [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)」を参照してください。  
  
## <a name="the-sqltrigger-attribute"></a>SqlTrigger 属性  
 
  `SqlTrigger` 属性は、トリガーとして登録する必要のあるメソッドを示します。  
  
 詳細については、「 [Sqltriggercontext](https://go.microsoft.com/fwlink/?LinkId=128022) 」と「 [sqltriggercontext](https://go.microsoft.com/fwlink/?LinkId=203898)」を参照してください。  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 SqlUserDefinedTypeAttribute をアセンブリのクラス定義に適用できます。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、これにより、このカスタム属性を持つクラス定義にバインドされたユーザー定義型が作成されます。  
  
 詳細については、「 [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)」を参照してください。  
  
## <a name="the-sqlmethod-attribute"></a>SqlMethod 属性  
 
  `SqlMethod` 属性は、UDT のメソッドまたはプロパティの決定性およびデータ アクセス プロパティを示すために使用します。  
  
 詳細については、「 [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義集計](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [CLR ユーザー定義関数](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR ユーザー定義型](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ストアドプロシージャ](../../../database-engine/dev-guide/clr-stored-procedures.md)   
 [CLR トリガー](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
