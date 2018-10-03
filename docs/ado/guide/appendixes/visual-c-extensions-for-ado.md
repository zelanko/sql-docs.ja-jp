---
title: ADO の visual C の拡張機能 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca21e976783a10a738488762e382982e4fd8fd8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747680"
---
# <a name="visual-c-extensions"></a>Visual C の拡張機能
Visual C で ADO のプログラミングの推奨される方法を使用して、 **#import**ディレクティブで説明したよう[Microsoft Visual C++ での ADO プログラミング](../../../ado/guide/appendixes/visual-c-ado-programming.md)します。 ただし、ADO の以前のバージョンに付属 Visual C を使用したプログラミングの代替方法: Visual C 拡張します。 このセクションでは、この機能をドキュメントにとって Visual C の拡張機能のコードを維持する必要がありますが、# を使用して新しい ADO コードを記述する必要があります**インポート**します。

 最も面倒なジョブ Visual C プログラマ顔 ADO を使用したデータを取得すると、データを C++ のデータ型の VARIANT データ型として返され、変換後のデータを格納するクラスまたは構造体が変換されるときの 1 つ。 面倒なだけ VARIANT データ型を C++ のデータを取得すると、パフォーマンスが低くなります。

 ADO では、バリアントを経由せずにネイティブの C/C++ データ型のデータの取得をサポートするインターフェイスを提供し、インターフェイスを使用して簡略化するプリプロセッサ マクロも提供します。 使いやすく、優れたパフォーマンス、柔軟なツールになります。

 内のレコードにバインドする C と C++ クライアント一般的では、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)C/C++ 構造体またはネイティブの C と C++ の型を含むクラスにします。 使用する場合、バリアント型から C と C++ ネイティブ型に変換コードを記述が含まれます。 ADO の Visual C の拡張は、Visual C のプログラマにとってこのシナリオをはるかに簡単に行う対象とします。

 ADO の Visual C の拡張の詳細については、次のトピックを参照してください。

-   [ADO の Visual C の拡張機能の使用](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Visual C++ Extensions のヘッダー](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [Visual C 拡張機能の例での ADO](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>参照
 [COM 用の Visual C 構文のインデックス用の ADO](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C の拡張機能の使用例](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual C の拡張機能を使用して](../../../ado/guide/appendixes/using-visual-c-extensions.md) [Visual C Extensions のヘッダー](../../../ado/guide/appendixes/visual-c-extensions-header.md)
