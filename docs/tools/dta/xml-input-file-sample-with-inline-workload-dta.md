---
title: XML 入力ファイルのサンプル インライン ワークロード (DTA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a8160ba2d7b3a0eebb5cf16411c232efe1a80ca
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a>インライン ワークロードを使用した XML 入力ファイルのサンプル (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]コピーして使用してワークロードを指定する XML 入力ファイルのこのサンプルを貼り付け、 **EventString**要素を使い慣れた XML エディターまたはテキスト エディターにします。 個別のワークロード ファイルを使用する代わりに、 **EventString** 要素を使用して XML 入力ファイル内の [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ワークロードを指定することができます。 このサンプルを編集ツールにコピーした後に、 **Server**、 **Database**、 **Schema**、 **Table**、 **Workload**、 **EventString**、および **TuningOptions** 要素で指定する値を、特定のチューニング セッションの値に置き換えてください。 これらの要素で使用できるすべての属性および子要素の詳細については、「 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)」を参照してください。 以下のサンプルでは、使用できる属性や子要素の一部だけを使用しています。  
  
## <a name="code"></a>コード  
 [!code-xml[InputFileSamples#InlineWorkloadInputFile](../../tools/dta/codesnippet/xml/xml-input-file-sample-wi_1.xml)]  
  
## <a name="comments"></a>コメント  
 `USE database_name` ステートメントは、 **EventString** 要素に含まれるインライン ワークロードで指定できます。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [データベース エンジン チューニング アドバイザーからの出力の表示および操作](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)   
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
