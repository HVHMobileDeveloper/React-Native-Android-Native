# React-Native-Android-Native
Adjust this code:

if (bundle.getString("message") == null) {
                // this happens when a 'data' notification is received - we do not synthesize a local notification in this case
                if (bundle.getString("google.message_id") != null){
                    Log.e(LOG_TAG, "message from google");
                    return;
                }
                if (bundle.getBoolean("foreground")){
                    Log.e(LOG_TAG,"Foreground is true will be return");
                    return;
                }
                Log.d(LOG_TAG, "Cannot send to notification centre because there is no 'message' field in: " + bundle);
                String md = bundle.getString("message_data");
                try {
                    JSONObject jsonObject = new JSONObject(md);
                    Log.e(LOG_TAG, String.valueOf(jsonObject));
                    JSONObject mo = jsonObject.getJSONObject("meta_data").getJSONObject("message_object");
                    String title = mo.getString("title");
                    String tag = mo.getString("broadcast_id");
                    bundle.putString("tag", tag);
                    bundle.putString("message", title);
                }catch (Exception ex){

                }
                //return;
            }
            
