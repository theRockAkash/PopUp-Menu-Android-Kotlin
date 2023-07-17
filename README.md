# PopUp-Menu-Android-Kotlin

```
private fun showPopup(v: View) {
        PopupMenu(v.context, v).apply {
            setOnMenuItemClickListener { item ->
                when (item?.itemId) {

                    R.id.edit -> {
                       //peform edit operation
                        true
                    }

                    R.id.delete -> {
                         //perform delete operation
                        true
                    }

                    else -> false
                }
            }
            inflate(R.menu.edit_delete_menu)
            show()
        }
    }
```
# PopUp Custom Layout Android Kotlin

```
   private fun showFilterLayout() {
        val popupBind = FilterLayoutBinding.inflate(layoutInflater)

        val popupWindow = PopupWindow(
            popupBind.root,
            binding.searchLayout.width,  //width of anchor view or custom width
            400,                        //hight of pop up view or custom hight
            true
        )
        val adapter = ArrayAdapter(
            this,
            R.layout.simple_spinner_item,
            listOf(
                "Alabama",
                "Alaska",
                "Arizona",
                "Arkansas",
                "California",
                "Colorado",
                "Connecticut",
                "Delaware"
            )
        )
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);
        popupBind.spinnerState.adapter = adapter
        popupBind.spinnerState.onItemSelectedListener =
            object : AdapterView.OnItemSelectedListener {
                override fun onItemSelected(
                    parent: AdapterView<*>?,
                    view: View?,
                    position: Int,
                    id: Long
                ) {
                    //do something with selected state
                }

                override fun onNothingSelected(parent: AdapterView<*>?) {}
            }
        popupBind.seekBar.setOnSeekBarChangeListener(object : SeekBar.OnSeekBarChangeListener {
            override fun onProgressChanged(p0: SeekBar?, p1: Int, p2: Boolean) {
                popupBind.tvDistance.text = "$p1 miles"
            }

            override fun onStartTrackingTouch(p0: SeekBar?) {

            }

            override fun onStopTrackingTouch(p0: SeekBar?) {

            }

        })
        popupBind.btLow.setOnClickListener {
            popupBind.btLow.setButtonEnabled(true)
            popupBind.btHigh.setButtonEnabled(false)
        }
        popupBind.btHigh.setOnClickListener {
            popupBind.btHigh.setButtonEnabled(true)
            popupBind.btLow.setButtonEnabled(false)

        }
        popupBind.btReset.setOnClickListener {
            popupWindow.dismiss()
        }
        popupBind.btApply.setOnClickListener {
            popupWindow.dismiss()
        }
        popupWindow.showAsDropDown(binding.searchLayout)  //pass anchor view
    }
```
