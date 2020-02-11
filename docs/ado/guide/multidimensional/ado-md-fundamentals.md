---
title: ADO MD の基礎 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 690c7b58c336596485b9ade77f0c02928853cd2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923203"
---
# <a name="ado-md-fundamentals"></a>ADO MD の基礎
Microsoft® ActiveX®データオブジェクト (多次元) (ADO MD) を使用すると、Microsoft Visual Basic®、Microsoft Visual C++®などの言語から多次元データに簡単にアクセスできます。 ADO MD により、Microsoft ActiveX® Data Objects (ADO) が拡張され、 [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)オブジェクトや[Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトなどの多次元データに固有のオブジェクトが含まれるようになります。 ADO MD を使用すると、多次元スキーマの参照、キューブのクエリ、および結果の取得を行うことができます。  
  
 ADO と同様に、ADO MD は、基になる OLE DB プロバイダーを使用してデータにアクセスします。 ADO MD を使用するには、プロバイダーが OLAP 仕様の OLE DB で定義されている多次元データプロバイダー (.MDP) である必要があります。 .MDP は、表形式のビューではなく、多次元ビューにデータを表示します。これは、表形式のデータプロバイダー (TDP) がデータを提示する方法です。 プロバイダーでサポートされている特定の構文と動作の詳細については、OLAP OLE DB プロバイダーのドキュメントを参照してください。  
  
 このドキュメントでは、Visual Basic プログラミング言語に関する実用的な知識と、ADO および OLAP に関する一般的な知識を前提としています。 詳細については、 [ADO プログラマーズガイド](../../../ado/guide/ado-programmer-s-guide.md)および[オンライン分析処理 (OLAP) の OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx)を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [多次元スキーマとデータの概要](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [多次元データの操作](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [ADO MD と ADO の併用](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [ADO MD を使用したプログラミング](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [ADO MD オブジェクトモデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO プログラマーズガイド](../../../ado/guide/ado-programmer-s-guide.md)   
 [データ定義言語およびセキュリティ用の ADO 拡張機能 (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [多次元スキーマとデータの概要](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [ADO MD を使用したプログラミング](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [ADO MD での ADO の使用](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [多次元データの操作](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
