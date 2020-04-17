---
title: ADO.NETでのユーザー定義型へのアクセス |マイクロソフトドキュメント
description: UDT は、.NET Framework CLR 言語で記述され、SQL Server データベースにオブジェクトとカスタム データ構造を格納できるようにします。 ADO.NETでは、プロバイダーが UDT を公開します。
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
ms.openlocfilehash: d14205a6fb506f5d4fddaac1ab601ff1ee9205b8
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488258"
---
# <a name="accessing-user-defined-types-in-adonet"></a>ADO.NET でのユーザー定義型へのアクセス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ユーザー定義型 (UDT) は、検証可能なコードを生成する[!INCLUDE[msCoName](../../includes/msconame-md.md)].NET Framework 共通言語ランタイム (CLR) でサポートされている言語のいずれかを使用して記述されます。 サポートされる言語には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などがあります。 UDT では、オブジェクトやカスタム データ構造を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納できます。 データは、.NET Framework のクラスまたは構造体のパブリック メンバーとして公開され、動作は .NET Framework のクラスまたは構造体のメソッドによって定義されます。 UDT は、テーブルの列定義、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチの変数、または [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数やストアド プロシージャの引数として使用することができます。  
  
 ADO.NETでは、**プロバイダー**は UDT を次の方法で公開します。  
  
-   オブジェクトとして**システム.データ.SqlClient.SqlDataReader**を介して。  
  
-   生のバイトとして**SqlDataReader**を介して。  
  
-   オブジェクトのパラメーターとして **。**  
  
## <a name="in-this-section"></a>このセクションの内容  
 [UDT データの取得](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 UDT データを取得する方法とパラメーターを指定する方法について説明します。  
  
 [データ アダプターによる UDT 列の更新](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 **データセット**で UDT を操作する方法と **、DataAdapter**を使用して UDT データを更新する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
