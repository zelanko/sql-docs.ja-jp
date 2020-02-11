---
title: CREATE TABLE ステートメントの制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db5d2cb8decde9828acd3005551717ac9f6cef32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096589"
---
# <a name="create-table-statement-limitations"></a>CREATE TABLE ステートメントの制限事項
Microsoft Access、Microsoft Excel、または Paradoxdriver が使用されていて、テキストまたはバイナリ列の長さが指定されていない (または0として指定されている) 場合、列の長さは255に設定されます。  
  
 DBASE ドライバーが使用されていて、text 列または binary 列の長さが指定されていない場合 (または0として指定されている場合)、列の長さは254に設定されます。  
  
 最大255列がサポートされています。  
  
 Microsoft Excel driver を MicrosoftExcel 5.0、7.0、または97データソースで使用する場合、以前に削除されたワークシートと同じ名前でワークシートを作成することはできません。 Microsoft Excel driver を使用してバージョン5.0、7.0、または97ワークシートにアクセスすると、DROP TABLE ステートメントによってワークシートがクリアされますが、ワークシート名は削除されません。  
  
 Paradox ドライバーを使用する場合、テーブルでインデックスが定義された後に列を追加することはできません。 CREATE TABLE ステートメントの引数リストの最初の列でインデックスが作成された場合、2番目の列を引数リストに含めることはできません。
