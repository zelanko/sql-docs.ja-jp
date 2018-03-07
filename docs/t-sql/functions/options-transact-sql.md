---
title: "@@OPTIONS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@OPTIONS'
- '@@OPTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, current SET options
- '@@OPTIONS function'
- current SET options
ms.assetid: 3d5c7f6e-157b-4231-bbb4-4645a11078b3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75919b6d27b2a81a9aba3575d3a9f3c54f0e0850
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40options-transact-sql"></a>&#x40;&#x40;ですオプション (TRANSACT-SQL)。
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在の SET オプションに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@OPTIONS  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 オプションは、の使用かられることができます、**設定**コマンドから、または、 **sp_configure ユーザー オプション**値。 セッションの値で構成されている、**設定**コマンドの上書き、 **sp_configure**オプション。 多くのツール (など[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]オプションの設定を自動的に構成します。 各ユーザーが、@@OPTIONS構成を表す関数。  
  
 SET ステートメントを使用することにより、特定のユーザー セッションの言語とクエリ処理オプションを変更できます。 **@@OPTIONS** を ON に設定されているオプションしか検出または OFF です。  
  
 **@@OPTIONS** 関数には、基本 10 (10 進数) 整数に変換された、オプションのビットマップが返されます。 ビット設定が、トピックの表で説明した場所に格納されている[user options サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)です。  
  
 デコードする、 **@@OPTIONS** 値、によって返された整数に変換**@@OPTIONS** を binary、次の表では、値を検索および[user options サーバー構成構成オプション](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)です。 たとえば場合、`SELECT @@OPTIONS;`値を返します`5496`、Windows のプログラマ電卓を使用して (**calc.exe**) 10 進数に変換する`5496`バイナリにします。 結果は `1010101111000`です。 右端の文字 (バイナリ 1、2、および 4) が 0 の場合、テーブル内の最初の 3 つの項目が無効になっていることを示すです。 表を参照することを確認、 **DISABLE_DEF_CNST_CHK**と**IMPLICIT_TRANSACTIONS**、および**CURSOR_CLOSE_ON_COMMIT**です。 次の項目 (**ANSI_WARNINGS**で、`1000`位置) にします。 ただしビット マップで作業左を続行し、オプションの一覧で下向きのです。 一番左にあるオプションが 0 の場合は、型変換によって切り捨てられます。 ビットマップ `1010101111000` は実際は `001010101111000` であり、全部で 15 個のオプションを表しています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-demonstration-of-how-changes-affect-behavior"></a>A. 変更が動作に与える影響の例  
 次の例での 2 つの異なる設定による連結動作の違い、 **CONCAT_NULL_YIELDS_NULL**オプション。  
  
```  
SELECT @@OPTIONS AS OriginalOptionsValue;  
SET CONCAT_NULL_YIELDS_NULL OFF;  
SELECT 'abc' + NULL AS ResultWhen_OFF, @@OPTIONS AS OptionsValueWhen_OFF;  
  
SET CONCAT_NULL_YIELDS_NULL ON;  
SELECT 'abc' + NULL AS ResultWhen_ON, @@OPTIONS AS OptionsValueWhen_ON;  
```  
  
### <a name="b-testing-a-client-nocount-setting"></a>B. クライアントの NOCOUNT 設定のテスト  
 次の例のセット`NOCOUNT``ON`の値をテストし、その`@@OPTIONS`です。 `NOCOUNT``ON`オプションを使用するセッションで各ステートメントについて、要求するクライアントに送信されるの影響を受ける行数に関するメッセージが表示されます。 `@@OPTIONS` の値は、`512` (0x0200) に設定されます。 これは NOCOUNT オプションを表します。 この例では、クライアントで NOCOUNT オプションが有効になっているかどうかを調べます。 たとえば、これはクライアントにおけるパフォーマンスの違いを調べるのに役立ちます。  
  
```  
SET NOCOUNT ON  
IF @@OPTIONS & 512 > 0   
RAISERROR ('Current user has SET NOCOUNT turned on.', 1, 1)  
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [user options サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)  
  
  
