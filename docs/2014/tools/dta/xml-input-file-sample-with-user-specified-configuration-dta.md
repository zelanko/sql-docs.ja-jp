---
title: ユーザー指定の構成を指定した XML 入力ファイルのサンプル (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: b29c9716-e5c3-4003-9efb-3ade2197b630
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4fefcec96100a9848810bc37a7b02760a3005cc3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63188098"
---
# <a name="xml-input-file-sample-with-user-specified-configuration-dta"></a>ユーザー指定の構成を指定した XML 入力ファイルのサンプル (DTA)
  この XML 入力ファイルのサンプルをコピーして、お使いの XML エディターまたはテキストエディターに**構成**要素を含むユーザー指定の構成を指定して貼り付けます。 これにより、"what-if" 分析を行うことができます。 "What-if" 分析では、 **Configuration** 要素を使用して、チューニング対象のデータベースに対して仮想的な物理設計構造のセットを指定します。 その後、データベース エンジン チューニング アドバイザーを使用して、この仮想的な構成に対してワークロードを実行した場合の影響を分析し、クエリ処理のパフォーマンスが向上するかどうかを調べます。 このタイプの分析には、実際に実装しなくても新しい構成を評価できるという利点があります。 仮想の構成で、期待したパフォーマンスの向上が得られなかった場合は、簡単に構成を変更でき、望ましい結果を生成する構成になるまで分析を繰り返し行えます。  
  
 このサンプルを編集ツールにコピーした後に、 **Server**、 **Database**、 **Schema**、 **Table**、 **Workload**、 **TuningOptions**、および **Configuration** 要素で指定する値を、特定のチューニング セッションの値に置き換えてください。 これらの要素で使用できるすべての属性および子要素の詳細については、「 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)」を参照してください。 以下のサンプルでは、使用できる属性や子要素の一部だけを使用しています。  
  
## <a name="code"></a>コード  
 [!code-xml[InputFileSamples#UserSpecifiedConfigInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#userspecifiedconfiginputfile)]  
  
## <a name="comments"></a>説明  
  
-   
  **Configuration** 要素に **Absolute** モードを指定した場合 (`Configuration SpecificationMode="Absolute"`)、物理設計構造の削除はサポートされません。  
  
-   
  **Configuration** 要素のいずれのモードでも ( **Relative**または **Absolute** )、同一の物理設計構造の作成と削除はできません。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [データベースエンジンチューニングアドバイザーからの出力を表示して操作する](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
