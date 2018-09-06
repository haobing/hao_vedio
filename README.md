# hao_vedio
HTTP Live Streaming直播关键技术步骤：

采集视频源和音频源的数据
对原始数据进行H264（视频）编码和AAC（音频）编码
视频和音频数据封装为MPEG-TS包
HLS分段生成策略及m3u8索引文件
HTTP传输协议

*一个网络中可以有多个TS流(用PAT中的ts_id区分)
 *  一个TS流中可以有多个频道(用PAT中的pnumber、pmt_pid区分)
 *  一个频道中可以有多个PES流(用PMT中的mpt_stream区分)
