---
title: ADO.NET | でのユーザー定義型へのアクセスMicrosoft Docs
description: .NET Framework CLR 言語で記述された Udt は、SQL Server データベースがオブジェクトとカスタムデータ構造を格納できるようにします。 ADO.NET では、プロバイダーは Udt を公開します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: cbbff72ab506238ec2134da8a91f91e3a315eb3f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727848"
---
# <a name="accessing-user-defined-types-in-adonet"></a>ADO.NET でのユーザー定義型へのアクセス
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  ユーザー定義型 (Udt) は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 検証可能なコードを生成する .NET Framework 共通言語ランタイム (CLR) でサポートされている言語のいずれかを使用して記述されます。 サポートされる言語には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などがあります。 UDT では、オブジェクトやカスタム データ構造を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納できます。 データは、.NET Framework のクラスまたは構造体のパブリック メンバーとして公開され、動作は .NET Framework のクラスまたは構造体のメソッドによって定義されます。 UDT は、テーブルの列定義、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチの変数、または [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数やストアド プロシージャの引数として使用することができます。  
  
 ADO.NET では、次の方法で**udt が公開**されます。  
  
-   オブジェクトとし**ての system.string**を使用します。  
  
-   **SqlDataReader**を生バイトとして使用します。  
  
-   **SqlParameter**オブジェクトのパラメーターとして指定します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [UDT データの取得](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 UDT データを取得する方法とパラメーターを指定する方法について説明します。  
  
 [データ アダプターによる UDT 列の更新](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 **データセット**内の udt を操作する方法と、 **dataadapter**を使用して udt データを更新する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
