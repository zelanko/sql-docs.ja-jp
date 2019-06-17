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
manager: craigg
ms.openlocfilehash: f5eab1c3bf6891f10c897966035dced2ffdc10ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63232210"
---
# <a name="create-table-statement-limitations"></a>CREATE TABLE ステートメントの制限事項
Microsoft Access、Microsoft Excel、または Paradoxdriver を使用すると、列の長さは 255 に設定して、テキストやバイナリ列の長さが指定されていない (または 0 として指定されます)。  
  
 DBASE ドライバーを使用すると、列の長さは 254 を設定して、テキストやバイナリ列の長さが指定されていない (または 0 として指定されます)。  
  
 最大 255 列がサポートされています。  
  
 MicrosoftExcel 5.0、7.0、または 97 データ ソース、ワークシート上の Microsoft Excel のドライバーを使用する場合は、以前に削除するワークシートと同じ名前で作成できません。 Microsoft Excel のドライバーを使用すると、バージョン 5.0、7.0、または 97 ワークシートにアクセスすると、DROP TABLE ステートメントは、ワークシートをクリアしますが、ワークシート名は削除されません。  
  
 Paradox ドライバーを使用すると、テーブルにインデックスを定義した後、この列を追加できません。 CREATE TABLE ステートメントの引数リストの最初の列は、インデックスを作成する場合は、引数リストの 2 番目の列を含めることができません。
