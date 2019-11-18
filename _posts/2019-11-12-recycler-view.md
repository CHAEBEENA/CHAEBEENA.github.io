---
title: "RecyclerView!"
date: 2019-11-20 08:26:28 -0400
categories: jekyll update
---

Fragment에 RecyclerView만들기 (Kotlin)



Adapter

```kotlin
package kr.co.gadaga.official.ui.faqimport android.transition.TransitionInflaterimport android.transition.TransitionManagerimport android.view.LayoutInflaterimport android.view.Viewimport android.view.ViewGroupimport androidx.recyclerview.widget.RecyclerViewimport kr.co.gadaga.official.Rimport kr.co.gadaga.official.data.model.Faqimport kr.co.gadaga.official.databinding.ItemFaqBindingclass FaqAdapter: RecyclerView.Adapter<FaqAdapter.FaqViewHolder>() {    
	var mList = mutableListOf<Faq>()  
    
    override fun getItemCount(): Int {        
        return mList.size    
    }    
    
    override fun onBindViewHolder(holder: FaqViewHolder, position: Int) { 
        holder.bind(mList[position])    
    }    
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): FaqViewHolder {        
        return FaqViewHolder(ItemFaqBinding.inflate(            LayoutInflater.from(parent.context),parent,false))    
    }    
    
    class FaqViewHolder(
        private val binding:ItemFaqBinding
    ) : RecyclerView.ViewHolder(binding.root) {      
        private var expanded = false        
        init {            
            val transition = TransitionInflater.from(itemView.context).inflateTransition(R.transition.info_card_toggle)            
            binding.titleContainer.setOnClickListener {                
                expanded = !expanded                
                transition.duration = if(expanded) 300L else 200L                TransitionManager.beginDelayedTransition(itemView.parent as ViewGroup, transition)                
                binding.cardDescription.visibility = if(expanded) View.VISIBLE else View.GONE                
                binding.expandIcon.rotationX = if(expanded) 180f else 0f            }        }        fun bind(item:Faq) {            
            binding.apply {                
                faq = item                
                executePendingBindings()            
            }        
        }    
    }
}
```



serious

ViewHolder

Fragment



Xml

Fragment_mypage

item_mypage

