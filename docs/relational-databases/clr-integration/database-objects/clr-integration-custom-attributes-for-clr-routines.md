---
title: CLR ルーチンのカスタム属性 |マイクロソフトドキュメント
description: カスタム属性は、CLR ルーチン、ユーザー定義型、および SQL Server に登録されているユーザー定義集計に適用できます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: a32a606f73858ede15569d1ade891ad2ce1c69a5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487958"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>CLR ルーチン用の CLR 統合のカスタム属性
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  一覧に示す属性は、 に登録された共通言語ランタイム (CLR) ルーチン、ユーザー定義型、およびユーザー定義集計に[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]適用できます。 属性が適用されない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は既定値を想定します。 一覧表示されている属性**は、名前空間**で定義されています。  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>属性を定義します。  
 属性**は**、メソッドがユーザー定義の集計として登録されることを示します。 すべてのユーザー定義集計にこのカスタム属性で注釈を付ける必要があります。  
  
 詳細については、「[を](https://go.microsoft.com/fwlink/?LinkId=124626)参照してください。  
  
## <a name="the-sqlfunction-attribute"></a>SqlFunction 属性  
 **SqlFunction**属性は、メソッドが適切な関数属性を設定して、関数として登録する必要があることを示します。  
  
 詳細については、「[属性」](https://go.microsoft.com/fwlink/?LinkId=128019)を参照してください。  
  
## <a name="the-sqlfacet-attribute"></a>属性  
 **SqlFacet**属性は、ユーザー定義型 (UDT) 式の戻り値の型に関する情報を返すために使用されます。  
  
 詳細については[、「SqlFacet 属性](https://go.microsoft.com/fwlink/?LinkId=128020)」を参照してください。  
  
## <a name="the-sqlprocedure-attribute"></a>SqlProcedure 属性  
 **SqlProcedure**属性は、メソッドをストアド プロシージャとして登録する必要があることを示します。 この属性は、Visual Studio だけで使用され、指定されたメソッドがストアド プロシージャとして自動的に登録されます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では使用されません。  
  
 詳細については、「[属性」を](https://go.microsoft.com/fwlink/?LinkId=128021)参照してください。  
  
## <a name="the-sqltrigger-attribute"></a>Sql トリガー属性  
 **SqlTrigger**属性は、メソッドをトリガーとして登録する必要があることを示します。  
  
 詳細については[、「Sql トリガー コンテキスト](https://go.microsoft.com/fwlink/?LinkId=128022)と[SqlTrigger 属性](https://go.microsoft.com/fwlink/?LinkId=203898)」を参照してください。  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 SqlUserDefinedTypeAttribute をアセンブリのクラス定義に適用できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、これにより、このカスタム属性を持つクラス定義にバインドされたユーザー定義型が作成されます。  
  
 詳細については、「[プロパティ情報」](https://go.microsoft.com/fwlink/?LinkId=128024)を参照してください。  
  
## <a name="the-sqlmethod-attribute"></a>SqlMethod 属性  
 **SqlMethod**属性は、UDT のメソッドまたはプロパティの決定性およびデータ アクセス プロパティを示すために使用されます。  
  
 詳細については、「[属性」を](https://go.microsoft.com/fwlink/?LinkId=128025)参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義集計](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [CLR ユーザー定義関数](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR ユーザー定義型](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ストアド プロシージャ](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [CLR トリガー](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
