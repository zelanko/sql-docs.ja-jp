---
description: ADO 用の Visual C++ Extensions
title: ADO の Visual C++ 拡張 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: rothja
ms.author: jroth
ms.openlocfilehash: a045c24989f058ae97aa9c7f4a29e27fb51acd02
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806480"
---
# <a name="visual-c-extensions-for-ado"></a>ADO 用の Visual C++ Extensions
Visual C++ で ADO をプログラミングする場合は、「 [Ado プログラミングの Microsoft Visual C++](./visual-c-ado-programming.md)」で説明されているように、 **#import**ディレクティブを使用することをお勧めします。 ただし、以前のバージョンの ADO には、Visual C++ を使用した別のプログラミング方法が付属しています。 Visual C++ の拡張機能です。 このセクションでは、Visual C++ の拡張機能のコードを維持する必要があるユーザー向けに、この機能について説明しますが、新しい ADO コードは #**import**を使用して記述する必要があります

 ADO を使用してデータを取得するときにプログラマが直面する最も面倒な Visual C++ ジョブの1つは、VARIANT データ型として返されたデータを C++ データ型に変換し、変換されたデータをクラスまたは構造体に格納することです。 複雑になるだけでなく、バリアントデータ型を使用して C++ データを取得すると、パフォーマンスが低下します。

 ADO には、バリアントを経由せずにネイティブの C/c + + データ型へのデータの取得をサポートするインターフェイスが用意されています。また、インターフェイスの使用を簡略化するプリプロセッサマクロも用意されています。 結果は柔軟なツールであり、使いやすく、パフォーマンスが優れています。

 C/c + + クライアントの一般的なシナリオでは、 [レコードセット](../../reference/ado-api/recordset-object-ado.md) 内のレコードを c/c + + 構造体またはネイティブ c/c + + 型を含むクラスにバインドします。 バリアントを使用する場合は、VARIANT から C/c + + ネイティブ型に変換コードを記述する必要があります。 ADO の Visual C++ 拡張機能は、このシナリオを Visual C++ プログラマーにとってはるかに簡単にすることを目的としています。

 ADO の Visual C++ 拡張機能の詳細については、次のトピックを参照してください。

-   [ADO の Visual C++ 拡張機能の使用](./using-visual-c-extensions.md)

-   [Visual C++ Extensions のヘッダー](./visual-c-extensions-header.md)

-   [Visual C++ 拡張機能を使用した ADO の例](./visual-c-extensions-example.md)

## <a name="see-also"></a>参照
 COM [Visual C++ extensions](./visual-c-extensions-example.md) [の ADO For Visual C++ 構文インデックス](../../reference/ado-api/ado-for-visual-c-syntax-index-for-com.md)Visual C++ 拡張 Visual C++[機能を使用し](./using-visual-c-extensions.md)た拡張機能[ヘッダー](./visual-c-extensions-header.md)の例