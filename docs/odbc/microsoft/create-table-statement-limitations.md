---
title: テーブル ステートメントの制限事項を作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7b54b56afb585aa1158394117ebae6cc78116de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899107"
---
# <a name="create-table-statement-limitations"></a>テーブル ステートメントの制限事項を作成します。
Microsoft Access、Microsoft Excel または Paradoxdriver 使用すると、列の長さは 255 に設定して、テキストやバイナリ列の長さが指定されていない (または 0 を指定)。  
  
 DBASE ドライバーを使用すると列の長さは 254 を設定して、テキストやバイナリ列の長さが指定されていない (または 0 を指定)。  
  
 最大 255 列はサポートされています。  
  
 MicrosoftExcel 5.0、7.0、または 97 データ ソース、ワークシート上の Microsoft Excel ドライバーを使用する場合は、以前に削除するワークシートと同じ名前で作成できません。 Excel ドライバーを使用して、バージョン 5.0、7.0、または 97 ワークシートにアクセスする、DROP TABLE ステートメントは、ワークシートのクリアが、ワークシート名は削除されません。  
  
 Paradox ドライバーを使用すると、インデックスをテーブルに定義した後、この列を追加できません。 CREATE TABLE ステートメントの引数リストの最初の列は、インデックスを作成する場合は、引数リストの 2 番目の列を含めることができません。
