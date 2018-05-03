---
title: ADO 用の visual C 拡張機能 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec4d71ac2c3027dbeb13630b5d8e034a9171f9bc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="visual-c-extensions"></a>Visual C の拡張機能
Visual C で ADO のプログラミングの推奨される方法を使用して、 **#import**で説明したように、ディレクティブ[C++ ADO プログラミングのビジュアル Microsoft](../../../ado/guide/appendixes/visual-c-ado-programming.md)です。 ただし、以前のバージョンの ADO 付属の Visual C を使用したプログラミングの別の方法: Visual C 拡張します。 このセクションでは、この機能を説明の Visual C の拡張機能のコードを保守する必要がありますが、# を使用して新しい ADO コードを記述する必要があります**インポート**です。

 最も面倒なジョブ Visual C プログラマ書体 ADO を使用してデータを取得すると、C++ のデータ型には VARIANT データ型として返され、クラスまたは構造体に変換後のデータを格納するデータが変換されるときの 1 つ。 だけでなく厄介で面倒、VARIANT データ型を使用して C++ データを取得すると、パフォーマンスが低くなります。

 ADO では、VARIANT を経由せずにネイティブの C/C++ データ型のデータの取得をサポートするインターフェイスを提供し、インターフェイスを使用して簡略化するプリプロセッサ マクロも提供します。 使いやすくするが、優れたパフォーマンス、柔軟なツールになります。

 一般的な C/C++ クライアント シナリオではバインド内のレコードを[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) C と C++ 構造体またはネイティブの C と C++ の型を含むクラスにします。 使用する場合、バリアント型から C と C++ ネイティブ型に変換コードの記述が含まれます。 ADO の Visual C 拡張は、Visual C プログラマにとって、このシナリオをはるかに簡単に行う対象とします。

 ADO の Visual C 拡張の詳細については、次のトピックを参照してください。

-   [ADO の Visual C の拡張機能の使用](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Visual C++ Extensions のヘッダー](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [拡張機能の使用例を Visual C で ADO](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>参照
 [COM 用の Visual C 構文のインデックスの ADO](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C 拡張機能の使用例](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual C の拡張機能を使用して](../../../ado/guide/appendixes/using-visual-c-extensions.md) [Visual C 拡張機能ヘッダー](../../../ado/guide/appendixes/visual-c-extensions-header.md)
