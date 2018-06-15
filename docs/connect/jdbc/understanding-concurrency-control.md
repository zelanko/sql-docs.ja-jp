---
title: 同時実行制御について |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 98b7dabe-9b12-4e1d-adeb-e5b5cb0c96f3
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71ca87537cef389ac6cedb47b21a39ce76ba1b97
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853217"
---
# <a name="understanding-concurrency-control"></a>同時実行制御をについてください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  同時実行制御とは、複数のユーザーが同時に行を更新しているときにデータベースの整合性を維持するために使用される、さまざまな手法を表します。 不適切な同時実行は、ダーティ リード、ファントム読み取り、反復不能読み取りなどの問題につながります。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]によって使用されるすべての同時実行手法へのインターフェイスを提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]をこれらの問題を解決します。  
  
> [!NOTE]  
>  詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同時実行性、同時実行データ アクセスの管理」を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="remarks"></a>解説  
 JDBC ドライバーは、以下に示す同時実行の種類をサポートしています。  
  
|同時実行の種類|特性|行ロック|Description|  
|----------------------|---------------------|---------------|-----------------|  
|CONCUR_READ_ONLY|[読み取り専用]|いいえ|カーソルを使用して更新することはできません。また、結果セットを構成する行にはロックが設定されません。|  
|CONCUR_UPDATABLE|オプティミスティック読み取り、書き込み|いいえ|データベースで、行の競合が発生する可能性が低いと想定されます。 行の整合性は、タイムスタンプの比較によって検証されます。|  
|CONCUR_SS_SCROLL_LOCKS|ペシミスティック読み取り、書き込み|はい|データベースで、行の競合が発生する可能性が高いと想定されます。 行の整合性は、行のロックによって保証されます。|  
|CONCUR_SS_OPTIMISTIC_CC|オプティミスティック読み取り、書き込み|いいえ|データベースで、行の競合が発生する可能性が低いと想定されます。 行の整合性は、タイムスタンプの比較によって検証されます。<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]し、後で、サーバーはこの変更 CONCUR_SS_OPTIMISTIC_CCVAL をテーブルに timestamp 列が含まれていない場合。<br /><br /> [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)]、OPTIMISTIC WITH VALUES が指定した場合でも、OPTIMISTIC WITH ROW VERSIONING が使用される基になるテーブルに timestamp 列がある場合。 OPTIMISTIC WITH ROW VERSIONING が指定されていて、テーブルにタイムスタンプがない場合は、OPTIMISTIC WITH VALUES が使用されます。|  
|CONCUR_SS_OPTIMISTIC_CCVAL|オプティミスティック読み取り、書き込み|いいえ|データベースで、行の競合が発生する可能性が低いと想定されます。 行の整合性は、行データの比較によって検証されます。|  
  
## <a name="result-sets-that-are-not-updateable"></a>更新不可能な結果セット  
 更新可能な結果セットは、行の挿入、更新、および削除が可能な結果セットです。 次の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]更新可能なカーソルを作成することはできません。 "結果セットは更新可能ではありません" という意味の例外が生成されます。  
  
|原因|Description|Remedy|  
|-----------|-----------------|------------|  
|ステートメントが JDBC 2.0 (以降) の構文を使用して作成されていない|JDBC 2.0 では、ステートメントを作成するための新しい方法が導入されました。 JDBC 1.0 の構文を使用した場合、結果セットは既定で読み取り専用になります。|ステートメントを作成するときに、結果セットの種類と同時実行を指定します。|  
|ステートメントが TYPE_SCROLL_INSENSITIVE を使用して作成されている|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 静的スナップショット カーソルを作成します。 このカーソルは、他のユーザーによる行の更新からカーソルを保護するために、基になるテーブル行から切り離されています。|TYPE_SCROLL_SENSITIVE、TYPE_SS_SCROLL_KEYSET、TYPE_SS_SCROLL_DYNAMIC、または TYPE_FORWARD_ONLY を CONCUR_UPDATABLE と共に使用し、静的カーソルが作成されないようにします。|  
|テーブル デザインにより KEYSET カーソルまたは DYNAMIC カーソルが使用できなくなっている|基になるテーブルが有効にする一意のキーを持っていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]する行を一意に識別します。|一意キーをテーブルに追加し、各行を一意に識別できるようにします。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
