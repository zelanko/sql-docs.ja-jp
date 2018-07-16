---
title: ADO.NET でのユーザー定義型へのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: 12
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6b48d45874824f166dc1b3843eda0e1052fddfd6
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354664"
---
# <a name="accessing-user-defined-types-in-adonet"></a>ADO.NET でのユーザー定義型へのアクセス
  サポートされる言語のいずれかを使用してユーザー定義型 (Udt) が記述された、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 共通言語ランタイム (CLR) 検証可能なコードを生成します。 サポートされる言語には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などがあります。 UDT では、オブジェクトやカスタム データ構造を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納できます。 データは、.NET Framework のクラスまたは構造体のパブリック メンバーとして公開され、動作は .NET Framework のクラスまたは構造体のメソッドによって定義されます。 UDT の変数として、テーブルの列の定義として使用できる、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、またはの引数として、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数またはストアド プロシージャ。  
  
 ADO.NET では、`System.Data.SqlClient` プロバイダーにより次の形態で UDT が公開されます。  
  
-   `System.Data.SqlClient.SqlDataReader` によりオブジェクトとして。  
  
-   `SqlDataReader` により生のバイト列として。  
  
-   `System.Data.SqlClient.SqlParameter` オブジェクトのパラメーターとして。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [UDT データの取得](accessing-user-defined-types-retrieving-udt-data.md)  
 UDT データを取得する方法とパラメーターを指定する方法について説明します。  
  
 [データ アダプターによる UDT 列の更新](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 `DataSets` 内の UDT を操作する方法と `DataAdapters` を使用して UDT データを更新する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](clr-user-defined-types.md)  
  
  
