---
title: 加解密
comments: 
date: 2024-06-29 17:53:29
updated: 2024-06-29 17:53:29
reward: 
description: 使用开发的加密工具
top_img: https://www.4kbizhi.com/d/file/2022/09/26/0948509cZbS.jpg
abbrlink:
---

{% tabs ctypro-list %}

<!-- tab CRC32 -->

<div class="crypto_CRC32" style="width: 400px;">
            <script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.min.js"></script>
            <script src="https://cdn.jsdelivr.net/gh/bencky1017/crypto/js/CRC32.js"></script>
            <div class="crypto1" style="width: 100%;max-width:400px;">
                <div class="crypto_title">
                    <h2>CRC32</h2>
                </div>
                <div class="input1">
                    <textarea name="input_block1" id="input_block1" cols="30" rows="4" placeholder="输入需要加解密的文本："
                        style="width: 99%;"></textarea>
                </div>
                <div class="crypto_button1">
                    <input type="button" class="btn1_1" value="加密" style="width: 99%;height: 60px;margin:10px 0px;">
                </div>
                <div class="output1">
                    <textarea name="output_block1" id="output_block1" cols="30" rows="4" placeholder="加解密结果："
                        style="width: 99%;"></textarea>
                </div>
                <div class="tips1">
                    字符长度：<span class="tips_span1">-</span>
                </div>
            </div>
            <script>
                $('.btn1_1').on('click', function () {
                    var get_val = $('#input_block1').val().trim()
                    // 此处使用不同的加密算法
                    var res_val = crc32(get_val)
                    $('#output_block1').val(res_val)
                    $('.tips_span1').text(res_val.length)
                });
            </script>
        </div>
<!-- endtab -->

<!-- tab Base64 -->
<div class="crypto_Base64" style="width: 400px;">
            <script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.min.js"></script>
            <script src="https://cdn.jsdelivr.net/gh/bencky1017/crypto/js/base64.js"></script>
            <div class="crypto2" style="width: 100%;max-width:400px;">
                <div class="crypto_title2">
                    <h2>Base64</h2>
                </div>
                <div class="input2">
                    <textarea name="input_block2" id="input_block2" cols="30" rows="4" placeholder="输入需要加解密的文本："
                        style="width: 99%;"></textarea>
                </div>
                <div class="crypto_button2">
                    <input type="button" class="btn2_1" value="加密" style="width: 49%;height: 60px;margin:10px 0px;">
                    <input type="button" class="btn2_2" value="解密" style="width: 49%;height: 60px;margin:10px 0px;">
                </div>
                <div class="output2">
                    <textarea name="output_block2" id="output_block2" cols="30" rows="4" placeholder="加解密结果："
                        style="width: 99%;"></textarea>
                </div>
                <div class="tips2">
                    字符长度：<span class="tips_span2">-</span>
                </div>
            </div>
            <script>
                $('.btn2_1').on('click', function () {
                    var get_val = $('#input_block2').val().trim();
                    // 此处使用不同的加密算法
                    var res_val = beu(get_val)
                    console.log(res_val)
                    $('#output_block2').val(res_val)
                    $('.tips_span2').text(res_val.length)
                });
                $('.btn2_2').on('click', function () {
                    var get_val = $('#input_block2').val().trim();
                    // 此处使用不同的加密算法
                    var res_val = bdu(get_val)
                    $('#output_block2').val(res_val)
                    $('.tips_span2').text(res_val.length)
                });
            </script>
        </div>
<!-- endtab -->

<!-- tab MD5/MDBK -->
<div class="crypto_MD5" style="width: 400px;">
            <script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.min.js"></script>
            <script src="https://cdn.jsdelivr.net/gh/bencky1017/crypto/js/md5.js"></script>
            <div class="crypto3" style="width: 100%;max-width:400px;">
                <div class="crypto_title3">
                    <h2>MD5/MDBK</h2>
                </div>
                <div class="input3">
                    <textarea name="input_block3" id="input_block3" cols="30" rows="4" placeholder="输入需要加解密的文本："
                        style="width: 99%;"></textarea>
                </div>
                <div class="type3">
                    <input type="radio" name="type3" id="md5" value="md5" checked>
                    <label for="md5">md5</label>
                    <input type="radio" name="type3" id="mdbk" value="mdbk">
                    <label for="mdbk">mdbk</label>
                </div>
                <div class="crypto_button3">
                    <input type="button" class="btn3_1" value="加密" style="width: 99%;height: 60px;margin:10px 0px;">
                </div>
                <div class="output3">
                    <textarea name="output_block3" id="output_block3" cols="30" rows="4" placeholder="加解密结果："
                        style="width: 99%;"></textarea>
                </div>
                <div class="tips3">
                    字符长度：<span class="tips_span3">-</span>
                </div>
            </div>
            <script>
                $('.btn3_1').on('click', function () {
                    var get_val = $('#input_block3').val().trim()
                    var type_val = $("input[name='type3']:checked").val();
                    // 此处使用不同的加密算法
                    var res_val = type_val == 'md5' ? md5(get_val) : mdbk(get_val)
                    $('#output_block3').val(res_val)
                    $('.tips_span3').text(res_val.length)
                })
            </script>
        </div>
<!-- endtab -->

{% endtabs %}